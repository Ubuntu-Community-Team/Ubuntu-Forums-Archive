---
title: "Problema al compartir partición NTFS con Windows 7"
date: 2012-06-28
forum: General Help
---

### Post by andresmaiden on 2012-06-28
Tengo un Ubuntu 12.04 en una notebook Samsung en su partición ext4. También tengo un Windows 7 en su partición y una tercera partición con NTFS que uso para compartir TODOS mis documentos entre los 2 sistemas operativos. Uso el 90% el Ubuntu, pero mi hija usa el Windows (solo para navegar y jugar al Sims).

Cuando usa el Windows y yo luego quiero volver a usar el Ubuntu, encuentro corruptos los últimos archivos que había usado en este Linux y no los puedo reparar o recuperar con este OS. Encontré que reiniciando en Windows y haciendo una reparación de la partición, me repara el problema y recupera alguno de los archivos. El tema está en que siempre me pierde alguno que directamente desaparece.

No encontré la causa de esto, ni mucho menos la solución y hoy perdí archivos importantes.

¿Se les ocurre algo que pueda hacer antes de que saque el Windows por completo?

Gracias y Saludos.
Andres Misiak

---

### Post by hunter.allen on 2012-07-02
Andrés,

Creo que el origen de este problema es la partición compartida. Si usted va a compartir una partición (no recomendable), usted debe utilizar el formato FAT32 (de esta manera Windows no se dañará nada, y tampoco lo hará de Linux).

Sin embargo, yo recomiendo un programa de sincronización de archivos, tales como Ubuntu One (viene instalado en su sistema) o Dropbox (no es difícil de encontrar en Google).

Espero que esto era útil para usted!

---

### Post by andresmaiden on 2012-07-04
Gracias hunter allen, voy a analizar cuánto realmente me sirve compartir la partición y probablemente pase toda la información a una ext3 o 4, porque realmente no lo estoy usando mucho eso (lo arrastro desde hace mucho este tipo de instalación) y sea más fácil y mejor que buscar el problema técnico que lo ocaciona.__

---

### Post by lisati on 2012-07-04
Our preferred language for the forum is English. If you want, one of the staff members can move your thread to a more appropriate section.

---

