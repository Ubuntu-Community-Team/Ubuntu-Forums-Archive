---
title: "How to know which component to install?"
date: 2006-04-23
forum: General Help
---

### Post by meepy on 2006-04-23
Hey everyone.

Could be posted in the wrong category, but I had trouble finding the right one. Okay, this is my question; while compiling various programs and applications, and an error appears and the compiling fails - like an error: openssl is not installed (etc, etc).

Okay I think, I just 'apt-get install openssl' - it installs without errors, but still while compiling the application it stops with the openssl? How do I know which package to install? What lib? What header? Is there some kind of page with information or other helpfull matrial? I see people on others post "Oh, you need libopenssl8-403-d" Where do they know that? (agressive exampel I know, hehe)

I don't know if it's me that's missing something, but I have trouble finding out what to install to make it compile flawless.

Thanks in advance :)

Best of luck, meep.

---

### Post by kh4nh on 2006-04-23
[QUOTE=meepy]Hey everyone.
Okay I think, I just 'apt-get install openssl' - it installs without errors, but still while compiling the application it stops with the openssl? How do I know which package to install? What lib? What header? Is there some kind of page with information or other helpfull matrial? I see people on others post "Oh, you need libopenssl8-403-d" Where do they know that? (agressive exampel I know, hehe)


Best of luck, meep.[/QUOTE]

when you run ./configure, if your system is missing any required component, it will spit out the message, that's one way to know.

The other way is to get on the website of the software that you are compiling, they always have info about dependencies for their software,

good luck

---

### Post by meepy on 2006-04-23
[QUOTE=kh4nh]when you run ./configure, if your system is missing any required component, it will spit out the message, that's one way to know.

The other way is to get on the website of the software that you are compiling, they always have info about dependencies for their software,

good luck[/QUOTE]

Ookay, thanks. Guess there is no other way around :)

---

### Post by Sef on 2006-04-23
If you know what to install or what you want to install go here:

[http://packages.ubuntu.com/breezy/]("http://packages.ubuntu.com/breezy/")

Once you find the package you want to install, type this:

sudo apt-get update

sudo apt-get install package-name  (You will see the package name in the window.)

---

