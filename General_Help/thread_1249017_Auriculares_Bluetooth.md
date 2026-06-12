---
title: "Auriculares Bluetooth"
date: 2009-08-24
forum: General Help
---

### Post by armendo.hollos on 2009-08-24
Buenas,
[INDENT]Es necesario:
[LIST]
[*]Bluez
[*]PulseAudio 0.9.13
[*]pavucontrol 
[/LIST]

En el directorio raíz (*/home/SuUsuario*) creamos un archivo de texto con el nombre: *.asoundrc*. Dentro de él vamos ha poner los datos del auricular.
Primero vincularlo normalmente y obtenemos el número de MAC ejecuantando en un terminar (Aplicaciones>accesorios>terminal) el comando : *hcitool scan*.
Dentro del *.asoundrc* colocamos:
[I]pcm.bluetooth {
[INDENT]type bluetooth
device "00:00:00:00:00:00"
}[/I][/INDENT]

Remplazando *"00:00:00:00:00:00"* por el valor que surgió al usar el comando anterior.
Seguido ejecutamos:
*pactl load-module module-alsa-sink device="bluetooth"*

Si salieron las cosas bien tiene que mostrar un número, con lo cual ya estamos listo para usarlo con Rhythmbox, por ejemplo.
Si no se escucha (mi caso), abrimos el *pavucontrol (PulseAudio Volume Control)* que se encuentra dentro de Aplicaciones>Sonido y video. En la solapa "output device" tiene que haber dos salida: placa de sonido y bluetooth.  Elegimos como Default el que deseamos, dentro del iconito con una flechita hacia abajo.
Espero que les funcione.
Referencias:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1152229](http://ubuntuforums.org/showthread.php?t=1152229)
[*][http://fosswire.com/post/2008/10/better-bluetooth-audio/](http://fosswire.com/post/2008/10/better-bluetooth-audio/)
[*][http://www.bluez.org/bluez-and-pulseaudio/](http://www.bluez.org/bluez-and-pulseaudio/)
[/LIST]
*No es robar, es sacar de un lado y poner en otro.*

Éxitos.
[/INDENT]
PD: Algunas imagenes.
[IMG]http://www.students.ic.unicamp.br/~ra016378/PulseAudioVolumeControl.png[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=113690&d=1242265004[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=113691&d=1242265004[/IMG]

---

