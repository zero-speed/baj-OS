
Este repositorio contiene el código fuente del Sistema Operativo BAJ-OS para el curso de "Sistemas operativos" 
de la serie [Writing an OS in Rust](https://os.phil-opp.com).

INTEGRANTES :
\Ayte Noa Alvaro Alonso 
\Quispe Chura, Jhon Efrain 
\Suca Hilares, Gabriel Caleb 

[post]: https://os.phil-opp.com/async-await/

**Consulta la [rama master](https://github.com/phil-opp/blog_os) para obtener más información.**

## Compilación

Este proyecto requiere una versión nightly de Rust porque utiliza algunas características inestables. Para compilarlo se necesita, como mínimo, la nightly _2020-07-15_. Puede que tengas que ejecutar `rustup update nightly --force` para actualizar a la nightly más reciente, incluso si faltan algunos componentes como `rustfmt`.

Puedes compilar el proyecto ejecutando:

```
cargo build
```

Para crear una imagen de disco arrancable a partir del kernel compilado, necesitas instalar la herramienta [`bootimage`]:

[`bootimage`]: https://github.com/rust-osdev/bootimage

```
cargo install bootimage
```

Después de instalarla, puedes crear la imagen de disco arrancable ejecutando:

```
cargo bootimage
```

Esto crea una imagen de disco arrancable en el directorio `target/x86_64-blog_os/debug`.

Abre un issue si tienes algún problema.

## Ejecución

Puedes ejecutar la imagen de disco en [QEMU] con:

[QEMU]: https://www.qemu.org/

```
cargo run
```

Para esto, deben estar instalados [QEMU] y la herramienta [`bootimage`].

También puedes escribir la imagen en una memoria USB para arrancarla en una máquina real. En Linux, el comando es:

```
dd if=target/x86_64-blog_os/debug/bootimage-blog_os.bin of=/dev/sdX && sync
```

Donde `sdX` es el nombre del dispositivo de tu memoria USB. **Ten cuidado** de elegir el nombre correcto del dispositivo, porque todo lo que haya en él será sobrescrito.

## Pruebas

Para ejecutar las pruebas unitarias y de integración, ejecuta `cargo xtest`.

## Licencia

Licenciado bajo una de las siguientes opciones:

- Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or
  http://www.apache.org/licenses/LICENSE-2.0)
- MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

según tu preferencia.

Ten en cuenta que esto solo aplica a esta rama de git; otras ramas podrían tener una licencia diferente.

### Contribución

Salvo que indiques explícitamente lo contrario, cualquier contribución enviada intencionalmente para su inclusión en este trabajo, según se define en la licencia Apache-2.0, se considerará licenciada de forma dual como se indica arriba, sin términos ni condiciones adicionales.
