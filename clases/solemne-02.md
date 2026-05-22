[link-p5js](https://editor.p5js.org/pavlosky/sketches/GnCdTUXrU)
Parece que este mensaje está en inglés
# Plantilla para solemne-02

## Agustín Bastidas Pablo Godoy

- (Agustín Bastidas) [cuentaGithub](https://github.com/agustinbastidas-pro)
- (Pablo Godoy) [cuentaGithub](https://github.com/pavloskyyy?fbclid=PAVERFWAR9gi1leHRuA2FlbQIxMABzcnRjBmFwcF9pZA8xMjQwMjQ1NzQyODc0MTQAAacbrZYrRCUBERdEqw3RNgZTDcM62ygVIE4RvcXeCLYeR2mCPQ6y_Unt8WZ9fw_aem_ZlE6GqyvTHVaQtuMWmMyhQ)

##“Club de Porros” es un álbum de Mamborap que refleja la vida urbana y la cultura juvenil desde una mirada relajada y callejera. Con beats lentos y una atmósfera “volada”, el proyecto mezcla temas como el consumo, la amistad y el escape de la rutina, convirtiéndose en un referente del rap underground
chileno.

![Portada de álbum](../encargos/club.jpg)

- (Club De Porros)
- 2011
- Mamborap
- Tracklist
M B R P
Piano Piano
M & M (ft. Mala Clase)
Mambotella
Freesfly
Prendo el Fazo
El Polo Sur Está Maldito
Protesta Rec
Encapuchao
Pinufn (Volar)
R.I.P. Terludio Nate Dogg
Clandestylo
Del Suelo al Cielo
Quiero
Club de Porros
Nos Vemo!



```txt
1. MBRP
2. Club de porros
3. Quiero
```

- Aspecto del álbum a desarrollar (premisa)

> Quisimos explorar cómo las letras reflejan el estilo artístico del álbum y la identidad de sus integrantes en ese período. Con ese objetivo, reinterpretamos sus diseños representándolos como humo proveniente de un cigarrillo de marihuana, elemento recurrente en las canciones. Esta idea se desarrolló mediante las cabezas de los personajes flotando en un espacio donde lleguen a interactuar entre ellas mediante a un rebote, y el cambio de expresiónes en las caras de los personajes, todo esto inspirado en el fondo del arte original del álbum.

## En conclusión, el resultado final se mantuvo fiel a la idea inicial planteada, logrando integrar de manera efectiva los elementos propuestos. Se consiguieron representar los personajes flotando e interactuando entre sí, así como incorporar cambios de expresión al pasar el cursor, lo que enriqueció la experiencia visual. De esta manera, se puede afirmar que los resultados obtenidos responden adecuadamente a los objetivos planteados desde un comienzo.

- Distancia entre premisa y resultado
> La verdad es que no mucha, la premisa fue en la misma direccion con el trabajo final

- Cosas no conseguidas
> Mejor rendimiento en la hitbox de las figuras

- Descubrimientos al trabajar

> remplazo de figuras junto a imagenes, tal para que las figuras sean la hitbox invicible y la imagen por encima de esta

## Explicación del código (3 aspectos)

### function preload() {
fondo = loadImage("./ladrillos_fondo.png");
for (let i = 1; i <= totalImagenes; i++) {


```js // La función "preload()" se ejecuta antes de que empiece el programa y sirve para cargar imágenes o archivos.
la funcion "loadImage()" carga imágenes desde la carpeta del proyecto.
la funcion imagenesBase guarda las imágenes normales.
"imagenesHover" guarda las imágenes que aparecen cuando el mouse pasa encima.
El "for" repite el proceso varias veces según "totalImagenes."
Esto permite tener pares de imágenes una imagen normal
una imagen interactiva (hover)

movimiento "posX" y "posY" son las posiciones y "velocidadX y velocidadY" controlan la rapidez. "dirX" y "dirY" indican si va hacia izquierda/derecha o arriba/abajo.

flotación - Usa funciones trigonométricas (sin y cos) para generar un movimiento suave tipo “flotando”. "frameCount" aumenta continuamente. "offset" evita que todos se muevan igual, asi el resultado es un movimiento orgánico y más natural.

### c.posX += c.velocidadX * c.dirX;
c.posY += c.velocidadY * c.dirY;

c.posX += sin(frameCount * 0.02 + c.offset) * 0.5;
c.posY += cos(frameCount * 0.02 + c.offset) * 0.5;

```movimiento "posX" y "posY" son las posiciones y "velocidadX y velocidadY" controlan la rapidez. "dirX" y "dirY" indican si va hacia izquierda/derecha o arriba/abajo.

flotación - Usa funciones trigonométricas (sin y cos) para generar un movimiento suave tipo “flotando”. "frameCount" aumenta continuamente. "offset" evita que todos se muevan igual, asi el resultado es un movimiento orgánico y más natural.
// Tu pedazo de código acá
```

### if (c.posX > width - c.r || c.posX < c.r) c.dirX *= -1;
if (c.posY > height - c.r || c.posY < c.r) c.dirY *= -1;
let dMouse = dist(mouseX, mouseY, c.posX, c.posY);


``` rebotes con hitbox real, hover - Esta parte detecta si el mouse está encima del círculo. se calcula la distancia entre la posición del mouse el centro del círculo
```

### Declaración sobre el uso de IA

- IA utilizada(s) y tipo de licencia (pago, gratuita)

> Chatgpt gratis

- Problema a resolver a través de la IA

> queriamos resolver el tema de movimiento libre de los personajes, el cambio de expresion por el tacto y arreglar el tema de la hitbox junto tacto del mouse

- Prompts utilizados

> chat gpt, necesito un prompt de p5.js de 5 circulos de estos colores, verde oscuro, verde claro, naranjo rojo yazul, que estos esten flotando en distintas direcciones, que estos circulos interactuan con las esquinas rebotando y chocando entre ellas, y que al pasar el mouse por encima de los circulos, cambian a un color mas oscuro

> ayudes a cambiar las pelotitas por imagenes, te comento que necesito 2 imagenes por cada pelotita, la base y la que cambia al pasar el cursor

> Prompt 3

- Secciones de código entregadas por la IA

```js
//let circles = [];

function setup() {
createCanvas(600, 600);

let colors = [
color(0, 100, 0), // verde oscuro
color(144, 238, 144),// verde claro
color(255, 140, 0), // naranjo
color(255, 50, 50), // rojo
color(50, 100, 255) // azul
];

for (let i = 0; i < 5; i++) {
circles.push({
x: random(width),
y: random(height),
dx: random(-3, 3),
dy: random(-3, 3),
r: 40,
baseColor: colors[i],
currentColor: colors[i]
});
}
}

function draw() {
background(240);

for (let i = 0; i < circles.length; i++) {
let c = circles[i];

// Movimiento
c.x += c.dx;
c.y += c.dy;

// Rebote en bordes
if (c.x < c.r || c.x > width - c.r) c.dx *= -1;
if (c.y < c.r || c.y > height - c.r) c.dy *= -1;

// Interacción con mouse (oscurecer)
let d = dist(mouseX, mouseY, c.x, c.y);
if (d < c.r) {
c.currentColor = color(
red(c.baseColor) * 0.6,
green(c.baseColor) * 0.6,
blue(c.baseColor) * 0.6
);
} else {
c.currentColor = c.baseColor;
}

// Dibujar
fill(c.currentColor);
noStroke();
circle(c.x, c.y, c.r * 2);
}

// Colisiones entre círculos
for (let i = 0; i < circles.length; i++) {
for (let j = i + 1; j < circles.length; j++) {
let a = circles[i];
let b = circles[j];

let d = dist(a.x, a.y, b.x, b.y);

if (d < a.r + b.r) {
// Intercambiar velocidades (rebote simple)
let tempDx = a.dx;
let tempDy = a.dy;

a.dx = b.dx;
a.dy = b.dy;

b.dx = tempDx;
b.dy = tempDy;
}
}
}
}
```
let circles = [];

function setup() {
createCanvas(600, 600);
noCursor();

// colores base
let colores = [
color(0, 100, 0), // verde oscuro
color(144, 238, 144), // verde claro
color(255, 140, 0), // naranjo
color(255, 50, 50), // rojo
color(50, 100, 255) // azul
];

// crear círculos
for (let i = 0; i < 5; i++) {
circles.push({
posX: random(width),
posY: random(height),
dirX: random([-1, 1]),
dirY: random([-1, 1]),
velocidadX: random(2, 5),
velocidadY: random(2, 5),
r: 40,
colorBase: colores[i],
colorActual: colores[i]
});
}
}

function draw() {
background(220);

for (let i = 0; i < circles.length; i++) {
let c = circles[i];

// movimiento (estilo dirX/dirY como tus ejemplos)
c.posX += c.velocidadX * c.dirX;
c.posY += c.velocidadY * c.dirY;

// rebote horizontal
if (c.posX > width - c.r || c.posX < c.r) {
c.dirX *= -1;
c.velocidadX = random(2, 5); // cambia velocidad
}

// rebote vertical
if (c.posY > height - c.r || c.posY < c.r) {
c.dirY *= -1;
c.velocidadY = random(2, 5); // cambia velocidad
}

// interacción mouse (oscurecer color)
let d = dist(mouseX, mouseY, c.posX, c.posY);

if (d < c.r) {
c.colorActual = color(
red(c.colorBase) * 0.6,
green(c.colorBase) * 0.6,
blue(c.colorBase) * 0.6
);
} else {
c.colorActual = c.colorBase;
}

// dibujar círculo
fill(c.colorActual);
noStroke();
ellipse(c.posX, c.posY, c.r * 2, c.r * 2);
}

// colisiones entre círculos (rebote simple)
for (let i = 0; i < circles.length; i++) {
for (let j = i + 1; j < circles.length; j++) {
let a = circles[i];
let b = circles[j];

let d = dist(a.posX, a.posY, b.posX, b.posY);

if (d < a.r + b.r) {
// intercambio de dirección (como lógica simple)
let tempDirX = a.dirX;
let tempDirY = a.dirY;

a.dirX = b.dirX;
a.dirY = b.dirY;

b.dirX = tempDirX;
b.dirY = tempDirY;
}
}
}
}

let objetos = [];

let imagenesBase = [];
let imagenesHover = [];

function preload() {
// cargar 5 pares de imágenes
for (let i = 1; i <= 5; i++) {
imagenesBase.push(loadImage("./img" + i + "_base.png"));
imagenesHover.push(loadImage("./img" + i + "_hover.png"));
}
}

function setup() {
createCanvas(600, 600);
noCursor();

for (let i = 0; i < 5; i++) {
objetos.push({
posX: random(width),
posY: random(height),
dirX: random([-1, 1]),
dirY: random([-1, 1]),
velocidadX: random(1, 2), // MÁS LENTO
velocidadY: random(1, 2), // MÁS LENTO
r: 40,
imgBase: imagenesBase[i],
imgHover: imagenesHover[i],
imgActual: imagenesBase[i]
});
}
}

function draw() {
background(220);

for (let i = 0; i < objetos.length; i++) {
let o = objetos[i];

// movimiento lento
o.posX += o.velocidadX * o.dirX;
o.posY += o.velocidadY * o.dirY;

// rebotes
if (o.posX > width - o.r || o.posX < o.r) {
o.dirX *= -1;
}

if (


