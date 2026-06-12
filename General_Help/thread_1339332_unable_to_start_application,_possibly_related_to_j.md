---
title: "unable to start application, possibly related to java trouble"
date: 2009-11-27
forum: General Help
---

### Post by Shooree on 2009-11-27
Hi. I was trying to fix an issue with java applications not working on my Karmic system, even though I have the medibuntu repo installed. I also tried installing java from java.com, which made firefox recognise it and work with it. However, I am still left unable to run java-made applications, which end up being opened by Gedit.

Today, all I want is to play Heroes of Newerth, a regular video game that I've been playing for ages now, launching it from a shortcut on the desktop. However, the game isn't being started, no processes are ran, etc. I looked at the shortcut's path, and tried running the game from terminal, which gives me:

```
shooree@shooree-laptop:~/Games/HoN$ sh hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: CHost::Init() - Unable to create shared OpenGL context

```

Doubleclicking hon.sh in Nautilus opens it in Gedit, although it has execute rights. Attempting to run the binary manually results in:

```
shooree@shooree-laptop:~/Games/HoN$ sh hon-x86
hon-x86: 1: Syntax error: "(" unexpected

```

I'm just not good at troubleshooting a problem such as this, but it is very very annoying, since now I can't do half the things I use my computer for. Neither java nor my favourite game work. Please share thoughts and comments.

---

### Post by Shooree on 2009-11-27
I just managed to get the java app running through terminal. Apparently, my syestem doesn't know what to run scripts with. How can that even be? How do I tell it that it should run them by default?

Anyway, the program started, but crashed. This is the terminal output:

```
shooree@shooree-laptop:~/SweetHome3D-2.1$ sh SweetHome3D 
Nov 27, 2009 6:07:20 PM java.util.prefs.FileSystemPreferences$2 run
INFO: Created user preferences directory.
Java 3D WARNING : reported GLX version = 1.2
    GLX version 1.3 or higher is required
    The reported version number may be incorrect.  There is a known
    ATI driver bug in glXQueryVersion that incorrectly reports the GLX
    version as 1.2 when it really is 1.3, so Java 3D will attempt to
    run anyway.
Canvas3D_createNewContext: couldn't create context
Error in Java 3D : 3 Renderer: Error creating Canvas3D graphics context
```

thoughts? I'm running the latest NVidia beta drivers that work flawlessly, btw. on an Acer Aspire 5920G laptop.

---

### Post by Ahadiel on 2009-11-27
> **Shooree said:**
> Hi. I was trying to fix an issue with java applications not working on my Karmic system, even though I have the medibuntu repo installed. I also tried installing java from java.com, which made firefox recognise it and work with it. However, I am still left unable to run java-made applications, which end up being opened by Gedit.

Today, all I want is to play Heroes of Newerth, a regular video game that I've been playing for ages now, launching it from a shortcut on the desktop. However, the game isn't being started, no processes are ran, etc. I looked at the shortcut's path, and tried running the game from terminal, which gives me:

```
shooree@shooree-laptop:~/Games/HoN$ sh hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: CHost::Init() - Unable to create shared OpenGL context

```

Doubleclicking hon.sh in Nautilus opens it in Gedit, although it has execute rights. Attempting to run the binary manually results in:

```
shooree@shooree-laptop:~/Games/HoN$ sh hon-x86
hon-x86: 1: Syntax error: "(" unexpected

```

I'm just not good at troubleshooting a problem such as this, but it is very very annoying, since now I can't do half the things I use my computer for. Neither java nor my favourite game work. Please share thoughts and comments.

I believe that hon-x86 is a binary... and therefore it should be run like so:
```
./hon-x86
```
or
```
/path/to/hon-x86
```

---

### Post by sn4re on 2010-01-22
> **Shooree said:**
> Today, all I want is to play Heroes of Newerth, a regular video game that I've been playing for ages now, launching it from a shortcut on the desktop. However, the game isn't being started, no processes are ran, etc. I looked at the shortcut's path, and tried running the game from terminal, which gives me:

```
shooree@shooree-laptop:~/Games/HoN$ sh hon.sh
warning: The VAD has been replaced by a hack pending a complete rewrite
K2 - Fatal Error: CHost::Init() - Unable to create shared OpenGL context

```
Did you ever get this fixed, and how? Since I'm currently having the same problem. Have been playing HoN for months, yet now it just stopped with this error message.

EDIT: Nevermind. Got it by reinstalling the video drivers.

---

