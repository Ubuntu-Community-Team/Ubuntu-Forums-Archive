---
title: "Permission via GUI for JDownloader"
date: 2011-10-05
forum: General Help
---

### Post by picknick on 2011-10-05
Hi everybody! I'm having trouble invoking gksudo in order to run a java command. I put the JDownloader launcher at the menu with the following command to execute the program:
```
sudo java -jar /home/mariano/.jd/JDownloader.jar
```
This launcher opens a terminal where sudo ask me the password and still open as long as JD is open too. What I want is to use gksudo instead of sudo so the terminal won't open and only the window (a GUI) pops up asking for the password.
I thought that this code would solve the issue but it didn't:
```
gksudo java -jar /home/mariano/.jd/JDownloader.jar
```
(I simply add "gk" before sudo)
When I run that launcher nothing happens. When I run that command in a terminal this is the output (*opción inválida=invalida option*):
```
mariano@mariano-laptop:~$ gksudo java -jar /home/mariano/.jd/JDownloader.jargksudo: opción inválida -- j
GKsu versión 2.0.2

Uso: gksudo [-u <usuario>] [opciones] <orden>

  --debug, -d
    Muestra información en pantalla que puede ser 
    útil para diagnosticar o resolver problemas.

  --user <usuario>, -u <usuario>
    Ejecuta <orden> como el usuario especificado.

  --disable-grab, -g
    Desactiva el «bloqueo» del teclado, ratón,
    y el foco mientras el programa esta preguntando por la
    contraseña
  --prompt, -P
    Pregunta al usuario si quiere que se bloquee su teclado
    y ratón antes de hacerlo.
  --preserv-env, -k
   Mantener las variables de entorno, estas no son $HOME
    ni $PATH, por ejemplo.
  --login, -l
    Actúa como un intérprete de órdenes de acceso. Esto puede
    causar problemas con Xauthority. ¡Debe ejecutar xhost
    para permitir que el usuario objetivo pueda abrir ventanas
    en su pantalla!

  --description <archivo|descripción>, -D  <archivo|descripción>
    Ofrece un nombre descriptivo para que la orden lo utilice
    como mensaje predeterminado, haciéndolo más agradable.
    También puede proporcionar la ruta absoluta a un archivo
    .desktop. Si lo hace, se utilizará clave «Name» del archivo.
  --message <mensaje>, -m <mensaje>
    Reemplaza el mensaje estándar que pregunta por la
    contraseña por el argumento indicado a la opción.
    Sólo debe utilizarlo si no es suficiente con 
    --description.

  --print-pass, -p
    Pide a gksu que pregunte la contraseña en la salida
    estándar como ssh-askpass. Útil cuando se usan guiones
    con programas que pueden recibir la contraseña por la
    entrada estándar.

  --sudo-mode, S
    Hace que GKSu utilice sudo en lugar de su, como si se le
    hubiera llamado como «gksudo».
  --su-mode, -w
    Hace que GKSu utilice su en lugar de utilizar el
    valor predeterminado de libgksu.

```

So, how can I use gksudo? Or, how can I avoid the terminal for give permission?

---

