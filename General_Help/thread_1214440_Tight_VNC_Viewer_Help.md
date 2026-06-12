---
title: "Tight VNC Viewer Help"
date: 2009-07-15
forum: General Help
---

### Post by carnivore1 on 2009-07-15
Hey all,

I am trying to get xtightvncviewer configured to work on Ubuntu..... acctually, xtightvncviewer is working quite well but I am trying to find a way to save the password for my connections so I do not have to type them in each time.

I did some looking around and I found the man pages section about this app....
```

Usage: xtightvncviewer [<OPTIONS>] [<HOST>][:<DISPLAY#>]
       xtightvncviewer [<OPTIONS>] [<HOST>][::<PORT#>]
       xtightvncviewer [<OPTIONS>] -listen [<DISPLAY#>]
       xtightvncviewer -help

<OPTIONS> are standard Xt options, or:
        -via <GATEWAY>
        -shared (set by default)
        -noshared
        -viewonly
        -fullscreen
        -noraiseonbeep
        -passwd <PASSWD-FILENAME> (standard VNC authentication)
        -encodings <ENCODING-LIST> (e.g. "tight copyrect")
        -bgr233
        -owncmap
        -truecolour
        -depth <DEPTH>
        -compresslevel <COMPRESS-VALUE> (0..9: 0-fast, 9-best)
        -quality <JPEG-QUALITY-VALUE> (0..9: 0-low, 9-high)
        -nojpeg
        -nocursorshape
        -x11cursor
        -autopass

```

With this info I created a launcher on the desktop with the following line in the Command Field....

```
xtightvncviewer 192.168.0.xx
```

Obviously, this will start the xtightvncviewer and try connecting to the listed IP address, but how do I get the password saved in this line. everytime I try to add it (in the wrong syntax i'm sure), it says something about the password file (which i can not find). everything I have found on google about this mysterious password file says it is in ~/etc/.vnc

So basicly, I guess what I am asking here is, can anyone give me an example of the correct syntax for the command line here or point me to the password file???


Thanks

---

### Post by litspliff on 2009-07-15
read this....

[http://www.tightvnc.com/vncpasswd.1.php](http://www.tightvnc.com/vncpasswd.1.php)

---

### Post by carnivore1 on 2009-07-15
Thanks for the quick reply litspliff, unfortunately that seems to be aimed at changing the password for vnc(Server) not vncViewer. unless of course I am not understanding it correctly.

In any case, I was unable to make anything from that page work for me. I simply what to create a shortcut on the desktop with the connection settings saved into it for each vncserver I am running on my LAN. Kind of like a make shift KVM :)

---

### Post by litspliff on 2009-07-17
it's my understanding that it doesn't work that way (-passwd password).
you have to point it at a password file (-passwd /placeonFS/passwdfile).

the link is for you to learn how to make/use the passwd file. without it, you just have to enter the passwd at a prompt, which is probably a better way of doing it anyhow due to security concerns. if you have a launcher with a plain-text password on your desktop, your asking for trouble.

i'm kinda a newb, but i use xtightvnc a lot. hopefully this helps you.

---

### Post by Pritamsng on 2009-07-24
Hi, All,
Actually i m trying to configure **[COLOR=#ff0000]vnc[/COLOR]** **[COLOR=#ff0000]server[/COLOR]**(multi user) on **[COLOR=#ff0000]ubuntu[/COLOR]**.. its working fine but one problem i m getting that is from the client system when i m connect to **[COLOR=#ff0000]server[/COLOR]** through **[COLOR=#ff0000]vnc[/COLOR]** i cant able to get the g[FONT=Times New Roman][SIZE=3]raphic.. a screen shoot i m attetching here. please any one can solve my prob then replay .[/SIZE][/FONT]
[IMG]http://i620.photobucket.com/albums/tt288/pritamsng/vncprob.jpg[/IMG][]("http://i620.photobucket.com/albums/tt288/p")

---

### Post by Pritamsng on 2009-07-24
hi > **Pritamsng said:**
> Hi, All,
Actually i m trying to configure **[COLOR=#ff0000]vnc[/COLOR]** **[COLOR=#ff0000]server[/COLOR]**(multi user) on **[COLOR=#ff0000]ubuntu[/COLOR]**.. its working fine but one problem i m getting that is from the client system when i m connect to **[COLOR=#ff0000]server[/COLOR]** through **[COLOR=#ff0000]vnc[/COLOR]** i cant able to get the g[FONT=Times New Roman][SIZE=3]raphic.. a screen shoot i m attetching here. please any one can solve my prob then replay .[/SIZE][/FONT]
[IMG]http://i620.photobucket.com/albums/tt288/pritamsng/vncprob.jpg[/IMG]

---

### Post by Pritamsng on 2010-02-10
He i got the solution,
just write "sh" in place of "exec"

---

