# Actividad 3 - Gestión Torneos Esports

## 1. Análisis del problema y requisitos del sistema

Este proyecto es un sistema de gestión de torneos de eSports que tiene como objetivo facilitar la organización y el desarrollo de torneos, permitiendo la gestión de equipos, jugadores, torneos, partidas y premios.

- **Actores:**

  - Administrador: Responsable de la gestión general del sistema.
  - Jugador: Participante en los equipos y torneos.

- **Funcionalidades Principales:**

  - **Administrador:** Registrar equipo, añadir jugadores a un equipo, consultar lista de equipos y jugadores, crear un torneo, inscribir equipos en torneo, generar parejas para partidas, registrar resultados de partida, actualizar clasificación, asignar premios a los ganadores.
  - **Jugador:** Consultar lista de equipos y jugadores, consultar clasificación en el torneo, participar en torneos y partidas.

  - **Relaciones entre Entidades:** Un equipo está compuesto por jugadores, un torneo tiene equipos, un torneo tiene partidas, una partida tiene un resultado, los ganadores reciben premios.

## 2. Diagrama de Casos de Uso:

**Descripción de casos de uso:**
  - Registrar equipo
    Este caso de uso permite al administrador del sistema crear un nuevo equipo. El objetivo es incorporar la información básica de un equipo para su participación en torneos. PAra iniciar, el sistema debe estar funcionando y el administrador debe haber iniciado sesión. El proceso prinicipal es que el administrador introuduce el nombre del equipo y una descripción opcional. Al confirmar, el sistema guarda esta información. Si el nombre ya existe, el sistema pide al administrador que elija otro. Finalmente el equipo queda registrado en el sistema.
  - Añadir jugadores a un equipo
    Este caso de uso permite al administrador asignar jugadores ya existentes a un equipo específico. El propósito es definir la composición de los equipos. Como requisitos previos, el sistema debe estar operativo, el administrador autenticado, y deben existir equipos y jugadores registrados. El administrador selecciona un equipo y luego elige a los jugadores disponibles para añadir. Tras la confirmación, el sistema actualiza la lista de miembros del equipo. Si no hay jugadores para añadir o si se intenta añadir uno que ya está en el equipo, el sistema informa al administrador. El resultado es que los jugadores seleccionados forman parte del equipo indicado.
  - Consulta lista de equipos y jugadores
    Este caso de uso permite al administrador (y posiblemente a los jugadores, con una vista limitada) acceder a la lista de todos los equipos y los jugadores que los integran. El objetivo es facilitar la visualización de la estructura de los equipos. El sistema debe estar en funcionamiento y el usuario autenticado, si es necesario. El sistema muestra un listado de los equipos, indicando el nombre de cada uno y sus jugadores. Si no hay equipos o un equipo no tiene jugadores, se muestra esta situación. El resultado es la visualización de la información solicitada.
  - Crear un torneo
    Este caso de uso permite al administrador configurar un nuevo torneo. El propósito es establecer los parámetros iniciales de la competición. El sistema debe estar operativo y el administrador autenticado. El administrador introduce el nombre del torneo, fecha de inicio, reglas y número máximo de equipos. Al guardar, el sistema crea el torneo con estos datos. El sistema puede realizar validaciones básicas sobre la información introducida. El resultado es la creación de un nuevo torneo en el sistema.
  - Inscribir equipos en torneo
    Este caso de uso permite al administrador registrar un equipo en un torneo específico. El objetivo es gestionar la participación de los equipos en las competiciones. El sistema debe estar operativo, el administrador autenticado, y deben existir equipos y torneos creados. El administrador selecciona un torneo y luego elige los equipos que desea inscribir. El sistema verifica si los equipos cumplen los criterios de inscripción y los añade a la lista de participantes del torneo. Se informa al administrador si un equipo ya está inscrito o no cumple los requisitos. El resultado es la inscripción de los equipos seleccionados en el torneo.
  - Generar parejas para partidas
    Este caso de uso permite al administrador crear los enfrentamientos entre los equipos inscritos en un torneo. El propósito es definir la estructura de las partidas. El sistema debe estar operativo, el administrador autenticado, y debe haber equipos inscritos en el torneo. El administrador selecciona un torneo y activa la generación de emparejamientos. El sistema aplica un algoritmo para formar las parejas de equipos que competirán. Los emparejamientos generados son almacenados y mostrados al administrador. El resultado es la creación de la programación de las partidas.
  - Registrar resultados de partida
    Este caso de uso permite al administrador introducir el resultado de un partido entre dos equipos en un torneo. El propósito es mantener un registro del desarrollo de la competición. El sistema debe estar operativo, el administrador autenticado, y debe existir la partida cuyo resultado se va a registrar. El administrador selecciona el torneo y la partida, introduce el resultado (indicando el ganador y opcionalmente la puntuación), y guarda la información. El sistema almacena este resultado. El resultado es el registro del desenlace del partido en el sistema.
  - Actualizar clasificación
    Este caso de uso permite al administrador actualizar la tabla de clasificación de un torneo basándose en los resultados de las partidas. El propósito es reflejar el progreso de los equipos. El sistema debe estar operativo, el administrador autenticado, y deben existir resultados de partidos registrados para el torneo. El administrador selecciona el torneo y activa la actualización. El sistema calcula la posición de los equipos según los criterios definidos y muestra la nueva clasificación. El resultado es la actualización de la tabla de clasificación del torneo.
  - Asignar premios a los ganadores
    Este caso de uso permite al administrador asignar los premios a los equipos que han ganado un torneo. El propósito es gestionar la entrega de recompensas. El sistema debe estar operativo, el administrador autenticado, y el torneo debe haber finalizado o los ganadores deben ser conocidos. El administrador selecciona el torneo, identifica a los ganadores y asigna los premios correspondientes. El sistema almacena esta información. El resultado es la asignación de los premios a los equipos ganadores.

**Diagrama de casos de uso para la Gestión de equipos y jugadores:**

  ![Gestión Equipos y Jugadores UML Showcase](/gestion_equipos_jugadores_esports.drawio.png)


## 3. Identificación de clases y relaciones

**Clases principales**
  EQUIPO

  JUGADOR

**Distinción Entidad, Control e Interfaz**

  Entidad: Equipo, Jugador

  Control: GestorEquipoJugador

  Interfaz: Consola para que el administrador gestione las funcionalidades

**Atributos de cada Clase**

  EQUIPO:

* nombreEquipo(String)
* descripcion (String, opcional)
* idEquipo (Identificador único, podría ser un entero o un UUID)
* jugadores (Una colección, como una lista, de objetos Jugador)
  
  JUGADOR:

* nombreJugador (String)
* idJugador (Identificador único, podría ser un entero o un UUID)
* nick (String, nombre de juego)

**Relaciones entre clases**
  EQUIPO:

  - addJugador
  - eliminarJugador
  - obtenerLista
  - getNombreEquipo
  - setNombreEquipo
  - getDescricion
  - setDescripcion
  - getIdEquipo

  JUGADOR:

  - getNombreJugador
  - setNombreJugador
  - getIdJugador

  GESTOREQUIPOJUGADOR:

  - registrarEquipo
  - addJugadorAEquipo
  - obtenerListaEquipos
  - obtenerEquiposPorId
  - obtenerJugadorPorId
  - obtenerJugadoresdeEquipo

- Asociaciones: Un Equipo está asociado con Jugador porque un equipo conoce a los jugadores que lo forman, y un jugador conoce a su equipo.

- Agreagaciones: El equipo tiene jugadores, pero si el equipo se disuelve, los jugadores seguirían existiendo como individuos en el sistema.

- Composiciones: Una ronda es una parte esencial de un torneo. Si el torneo no existe, las rondas tampoco tienen sentido en ese contexto específico.

![Diagrama de Clases UML Showcase](/diagrama_clases_actividad3.drawio.png)

Se identifican tres clases principales: Equipo, Jugador y GestorEquipoJugador. Las clases Equipo y Jugador actúan como entidades, modelando los datos esenciales del sistema. La clase Equipo contiene atributos como el nombre, descripción, un identificador único y una colección de objetos Jugador, reflejando la composición de un equipo. La clase Jugador almacena información como el nombre y un identificador único.

La relación entre Equipo y Jugador se establece mediante una asociación con una cardinalidad de uno a muchos (1 \*), indicando que un equipo puede tener múltiples jugadores asociados.

La clase GestorEquipoJugador actúa como una clase de control, encargada de las operaciones relacionadas con equipos y jugadores. Se observa una relación de dependencia desde GestorEquipoJugador hacia las clases Equipo y Jugador. Los métodos de GestorEquipoJugador utilizan instancias de Equipo y Jugador para implementar funcionalidades como el registro de equipos y la asignación de jugadores.

### Autora

[Tanimara Elias Santos](https://github.com/tanimaraeliassantos)

### Versión

1.0.0
