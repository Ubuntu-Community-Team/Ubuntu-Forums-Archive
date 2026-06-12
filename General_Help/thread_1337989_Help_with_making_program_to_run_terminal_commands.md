---
title: "Help with making program to run terminal commands"
date: 2009-11-26
forum: General Help
---

### Post by Holder350 on 2009-11-26
I need something simple that will run 2 commands in the terminal.

I have finaly gotten my Svideo on my laptop working, but for it to work I have to open terminal and input

```
sudo xrandr --output S-video --set load_detection 1

Sudo xrandr --output S-video --mode 800x600
```But when I disconnect then reconnect I have to run it again to make it work again.

I am wanting an Icon to put in a menu so I can click and it will run the commands for me without having to input it every time.

I know this must be something simple, but I am a new Linux user (long time Windows geek) and I am pulling my hair out......ANY input would be helpful.

Also, if this is in the wrong section I apologize. I didn't know what catagory this might fall under

[info]
Dell Inspiron 8500
Ubuntu 9.10
ATI Radeon 9000
[info/]

---

### Post by dcstar on 2009-11-26
> **Holder350 said:**
> I need something simple that will run 2 commands in the terminal.

I have finaly gotten my Svideo on my laptop working, but for it to work I have to open terminal and input

```
sudo xrandr --output S-video --set load_detection 1

Sudo xrandr --output S-video --mode 800x600
```But when I disconnect then reconnect I have to run it again to make it work again.

I am wanting an Icon to put in a menu so I can click and it will run the commands for me without having to input it every time.
.......

Create a text file (somewhere convenient) in your home folder, put those commands in it and then make the file Executable.

Create a launcher on your Desktop pointing to that filename (with the full path).

---

### Post by Holder350 on 2009-11-26
Thank you sir!! Works great!

---

