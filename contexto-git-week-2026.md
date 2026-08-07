# Contexto del proyecto — 2º GIT WEEK 2026

> Pega este archivo completo al inicio de un chat nuevo (o dile a Claude que lo lea desde esta ruta usando el MCP de filesystem) para tener todo el contexto sin repetir el historial previo.

## 1. Qué es el proyecto
Sitio web para el **2º GIT WEEK 2026**, congreso nacional organizado por **GIT Construcción UNI** (Universidad Nacional de Ingeniería), en el marco del **150 aniversario de la UNI**. JJ coordina el desarrollo web, dependiendo de contenido de dos áreas: **Marketing** (identidad visual, difusión) y **Relaciones Exteriores** (ponentes, sponsors).

## 2. Datos del evento
- **Nombre oficial:** 2º GIT WEEK 2026
- **Fechas:** 29, 30 y 31 de octubre de 2026
- **Lema/hashtag:** #ConstruyendoOportunidades
- **Ejes temáticos:** BIM · LEAN · VDC · PMI
- **Mascota oficial:** leopardo/jaguar bebé con casco de construcción con logo GIT

## 3. Identidad visual

### Paleta de colores
- **Paleta GIT UNI:** Azul `#1D4E89` (aprox), negro, azul oscuro `#0B2545`
- **Paleta Aniversario UNI:** Guinda/vino `#7A1B2C`, dorado/beige `#C9A24B`, blanco hueso `#F4EFE3`

### Tipografías (Google Fonts)
- **Títulos:** Barlow SemiCondensed
- **Subtítulos:** League Spartan / Poppins
- **Textura (a criterio):** Quicksand

## 4. Estructura real de archivos
```
git-week-2026/
├── index.html
├── README.md
├── contexto-git-week-2026.md
├── .gitattributes
└── assets/
    ├── img/
    │   ├── logos/
    │   │   ├── logo-uni.png
    │   │   ├── logo-git-negro.png   ← usado en nav y footer (sobre chip blanco)
    │   │   ├── logo-git-blanco.png  ← reservado para fondos oscuros SIN chip blanco
    │   │   └── logo-150-uni.png
    │   ├── mascota/
    │   │   ├── mascota.png           ← de repuesto, no se usa actualmente
    │   │   └── poster-git-week.png   ← EN USO en el hero (versión transparente)
    │   ├── iconos/
    │   │   ├── icono-bim.png    (64px en la card, tamaño base)
    │   │   ├── icono-lean.png   (82px, clase .icono-md)
    │   │   ├── icono-vdc.png    (120px, clase .icono-grande, es el más grande)
    │   │   └── icono-pmi.png    (82px, clase .icono-md)
    │   ├── ponentes/  (vacía, esperando fotos de Relaciones Exteriores)
    │   └── sponsors/  (vacía, esperando logos de sponsors)
    └── video/
        └── video-institucional.mp4  ← comprimido con HandBrake (720p), EN USO en sección "¿Qué es GIT?"
```

### Nota técnica — tarjetas de "¿Qué es GIT?" (BIM/LEAN/VDC/PMI)
Cada ícono va dentro de un contenedor `.eje-icono-box` de altura fija (130px) con `display:flex;align-items:center;justify-content:center`. Esto es a propósito: como los 4 íconos tienen tamaños distintos (64/82/120px) para respetar sus proporciones originales, sin esa caja de altura fija los títulos quedaban a distinta altura entre tarjetas (se veía disparejo). No cambiar esto sin mantener el mismo mecanismo.

### Nota técnica — footer
Los logos del footer van dentro de una "tarjeta" blanca (`background:#fff;border-radius:10px;padding:8px 14px`) sobre el fondo azul oscuro, para que se vean con contraste sin importar el color del logo. No usar filtros CSS tipo `invert()` ahí, ya causó bugs antes (logo se veía como cuadro blanco vacío).

### Nota técnica — video institucional
Ya NO es un link a Drive. Está embebido directo con `<video controls>` apuntando a `assets/video/video-institucional.mp4`. Se reproduce nativo en la página, sin salir a otra pestaña.

## 5. Redes sociales y contacto (CONFIRMADOS Y CARGADOS EN EL CÓDIGO)
| Canal | Dato |
|---|---|
| Facebook | https://www.facebook.com/gitconstruccion.uni |
| Instagram | https://www.instagram.com/gitconstruccion.uni/ |
| YouTube | https://www.youtube.com/@gitconstruccion-uni |
| LinkedIn | https://www.linkedin.com/company/git-construcci%C3%B3n-uni/posts/?feedView=all |
| Correo oficial | gitconstruccion@uni.edu.pe |

## 6. Paquetes de inscripción
| Plan | Precio | Estado |
|---|---|---|
| 🔵 General | Por confirmar (Logística) | Nombre definitivo (reemplaza a "Entrada Libre") |
| 🟡 Professional | Por confirmar (Logística) | Nombre definitivo (reemplaza a "Normal"), destacado visualmente en la web |
| 🔴 Executive | Por confirmar (Logística) | Nombre definitivo (reemplaza a "Premium") |

Descripciones ya cargadas en el HTML:
- **General:** Acceso a ceremonias, feria empresarial y masterclass (ponencias).
- **Professional:** Incluye todo lo del plan General, Kit de Bienvenida y taller de empleabilidad.
- **Executive:** Incluye acceso completo, visita técnica, networking preferencial y beneficios especiales.

Colores de los badges en el cronograma (ya alineados con los emojis de las tarjetas): General = azul, Professional = amarillo/dorado, Executive = rojo. Internamente en el código las claves siguen llamándose `libre` (=General), `normal` (=Professional), `premium` (=Executive) — son solo nombres de variable, no afectan lo que se ve en pantalla.

**Botón de inscripción:** ya existe un botón grande y llamativo (dorado, debajo de las tarjetas de planes) con el texto "✍️ Inscríbete al 2º GIT Week 2026". Tiene un comentario en el HTML marcando exactamente dónde pegar el link real del formulario (Google Forms) cuando Logística lo envíe — buscar el comentario `<!-- AQUÍ VA EL LINK DEL FORMULARIO DE INSCRIPCIÓN... -->` cerca del final de la sección de inscripción.

Ventas no se muestran hasta aprox. el 19 (mes por confirmar). Sección en "Coming Soon". El botón de inscripción llevará a un formulario que redirige a un grupo de WhatsApp tras el pago (gestión de Logística) — sin lógica de login/desbloqueo por ahora.

## 7. Cronograma (ACTUALIZADO — datos confirmados)
Tres bloques por día (29, 30, 31 de octubre): **Actividades institucionales**, **Ponencias y paneles**, **Concursos**. Datos completos en el objeto `cronogramaData` dentro del `<script>` de `index.html`, con tabs funcionales por día.

### Actividades institucionales
| Día | Hora | Actividad | Plan |
|---|---|---|---|
| Jueves 29 | 8:00 - 12:00 | Visita técnica masiva (colegio) | 🔴 Executive |
| Jueves 29 | 14:00 - 15:00 | Ceremonia de inauguración | 🔵 General |
| Viernes 30 | 9:00 - 12:00 | Workshop de constructoras / softwares / capacitadoras | 🟡 Professional |
| Viernes 30 | 14:00 - 16:00 | Workshop de constructoras / softwares / capacitadoras | 🟡 Professional |
| Sábado 31 | 10:30 - 12:00 | Ceremonia de premiación | 🔵 General |

### Ponencias y paneles
| Día | Hora | Actividad | Plan |
|---|---|---|---|
| Jueves 29 | 15:30 - 17:30 | Masterclass VDC / IPD | 🔵 General |
| Jueves 29 | 18:00 - 20:00 | Masterclass BIM | 🔵 General |
| Viernes 30 | 8:30 - 10:30 | Masterclass PMI | 🔵 General |
| Viernes 30 | 15:30 - 17:30 | Masterclass Modern Construction | 🔵 General |
| Viernes 30 | 18:00 - 20:00 | Masterclass Lean | 🔵 General |
| Sábado 31 | 8:30 - 10:30 | Taller de empleabilidad | 🟡 Professional |

### Concursos
| Día | Hora | Actividad | Plan |
|---|---|---|---|
| Jueves 29 | 15:00 - 18:00 | Concurso LEAN (organizado por LSN) | 🔴 Executive |
| Viernes 30 | 14:30 - 18:30 | Concurso de ponencias estudiantiles (Categoría A y B) | 🟡 Professional |

**Sábado 31 NO tiene concursos** (se eliminó un dato incorrecto que estaba puesto ahí antes).

⚠️ **Pendiente de confirmar con JJ/Logística:** el plan asignado a Workshop, Taller de empleabilidad y Concurso de ponencias estudiantiles (quedaron en Professional por continuidad con la versión anterior, pero no se confirmó explícitamente como se hizo con Visita técnica y Concurso LEAN, que SÍ se confirmaron como Executive). Revisar fila por fila antes de darlo por cerrado.

## 8. Reparto de responsabilidades
| Tema | Responsable |
|---|---|
| Identidad visual, flyers, redes, videos institucionales | **Marketing** |
| Ponentes, sponsors, alianzas | **Relaciones Exteriores** |
| Precios finales de los 3 planes, premios/reconocimientos | **Logística** |
| Correo/WhatsApp de contacto para empresas | **RRHH** (aún no existe) |
| Imagen institucional FIC/UNI | **Presidencia** |

## 9. Estado del sitio web — ETAPA 2 CERRADA ✅ (GitHub + hosting) + correcciones de contenido en curso
- **Etapa 1 (contenido base):** `index.html` funcional con logos, íconos, poster, video, redes, correo, countdown, cronograma con tabs, flip cards de ponentes/sponsors (vacías), sección de inscripción en "Coming Soon".
- **Etapa 2 (publicación):** repositorio creado y conectado en GitHub (`orlanduhni/git-week-2026`, público), sincronizado en tiempo real con GitHub Desktop desde la carpeta local. **GitHub Pages activado y en vivo.**
- **Link público del sitio:** https://orlanduhni.github.io/git-week-2026/
- **Cronograma corregido** (ver sección 7) con horas y nombres reales de actividades, más badges de plan (General/Professional/Executive) coloreados según el plan real de cada actividad.
- **Botón grande de inscripción** agregado, con placeholder listo para el link del Forms.
- ⚠️ **Al cierre de este chat (6 de agosto 2026), GitHub tuvo un incidente reportado oficialmente en githubstatus.com afectando GitHub Actions** (los deploys de Pages se quedaban en cola o fallaban por falta de capacidad, sin relación con el código del sitio). Los últimos cambios (badges Executive de Visita técnica y Concurso LEAN) quedaron commiteados localmente pero el deploy puede no haberse completado — **revisar en el próximo chat si el push ya se reflejó en la web en vivo, y si no, solo hace falta esperar a que el incidente se resuelva y volver a intentar el push/deploy (no es un error del código).**
- **Pendiente real (para Etapa 3):** fotos de ponentes, logos de sponsors, precios finales de los 3 planes.

## 10. Flujo de trabajo con GitHub Desktop (IMPORTANTE — leer antes de tocar el repo)
JJ trabaja con **GitHub Desktop** (no terminal, no comandos escritos). El ciclo para publicar cualquier cambio es siempre el mismo, 3 pasos:

1. **Editar** los archivos normal en la carpeta local (`C:\Users\2025\Desktop\CURSOS\UNI\git-week-2026`).
2. **Commit:** en GitHub Desktop, pestaña "Changes" → escribir un mensaje corto en "Summary" → botón "Commit to main" (o Ctrl+Enter). Esto guarda el cambio SOLO en la computadora, todavía no en internet.
3. **Push:** botón "Push origin" arriba (o Ctrl+P). Esto sí sube el cambio a GitHub.com. **Sin este paso, la web pública NO se actualiza**, aunque el commit ya esté hecho — GitHub Pages construye el sitio leyendo GitHub.com, no la computadora local.

### Errores ya resueltos, no repetir:
- **No usar "Clone repository"** sobre una carpeta que ya tiene contenido: crea una subcarpeta anidada vacía con el mismo nombre (pasó una vez, causó confusión). Para una carpeta local ya existente con archivos, usar siempre **"File → Add local repository"** y, si pide, **"create a repository here"**.
- Si el repo local no logra conectarse al remoto ya creado en GitHub.com (error "name already exists"), el camino más simple (sin usar comandos de terminal) es borrar el repo vacío en la web (Settings → Danger Zone → Delete) y volver a darle "Publish repository" desde Desktop — así lo crea y lo vincula en un solo paso.
- El repo debe estar en **Público** (no Privado) para que GitHub Pages gratuito funcione.

## 11. Hosting — GitHub Pages (decisión ya tomada)
Se descartó la idea de "14 días de prueba gratis": esa condición NO aplica a GitHub Pages, Netlify o Vercel para sitios estáticos como este — son gratis indefinidamente, sin tarjeta de crédito, sin expiración. Se eligió **GitHub Pages** por ser lo más directo dado que el repo ya vive en GitHub (Settings → Pages → Deploy from a branch → main → /root).

Actualizar la web es automático: cualquier push a la rama `main` dispara un rebuild de GitHub Pages en 1-3 minutos, sin acción manual adicional.

## 12. SIGUIENTE FASE — Fase 3 (aún no empezada)
Objetivo de la Fase 3: reemplazar los placeholders reales una vez llegue el contenido de las áreas correspondientes.
- **Ponentes y sponsors:** esperando datos homogéneos de Relaciones Exteriores (JJ definirá con ellos un día fijo por semana de envío). Falta crear un formulario estándar (Google Forms u otro) con campos fijos para que manden la info ya lista para subir sin pedir manualmente cada vez.
- **Precios de los 3 planes** (Entrada Libre / Normal / Premium): pendientes de Logística.
- Reemplazar en `index.html` las flip cards vacías de ponentes/sponsors y quitar el "Coming Soon" de inscripción cuando haya precios y fecha de apertura de ventas confirmada (aprox. el día 19, mes por confirmar).
- Evaluar conectar un dominio propio (opcional, no urgente) y registrar el sitio en Google Search Console para indexación en buscadores (opcional, no urgente, el sitio ya funciona por link directo).

## 13. Plan técnico general
- Acceso directo a la carpeta local vía MCP de filesystem: `C:\Users\2025\Desktop\CURSOS\UNI\git-week-2026`
- Repo GitHub: `orlanduhni/git-week-2026` (público), sincronizado con GitHub Desktop
- Sitio en vivo: https://orlanduhni.github.io/git-week-2026/
- JJ también usa un script propio en Python + Gemini API para generar descripciones de imágenes al subirlas — corre local, independiente del hosting, antes de hacer commit.
