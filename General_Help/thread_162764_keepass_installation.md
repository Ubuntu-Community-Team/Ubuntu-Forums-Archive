---
title: "keepass installation"
date: 2006-04-19
forum: General Help
---

### Post by kroiz on 2006-04-19
Hi, I am tring to get keepass (password manager) to work.

I downloaded it from [http://keepass.berlios.de/index.php?lang=english]("http://keepass.berlios.de/index.php?lang=english")
then I did:
 ```
sudo dpkg -i KeePassX-0.2.0.deb
```
then when I tried running it I got:
```
keepass: error while loading shared libraries: libQt3Support.so.4: cannot open shared object file: No such file or directory
```
so I used synaptic to install libQt3Support.

now when I try running it, it says
```
keepass: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
```

the libpng3 description in synaptic state that this package has been superseded by libpng12. :-k so I steped back from my computer and decided to ask you for advice.:D

should I just go ahead and installs libs until It works? or can I do damage to other installed packages?

---

### Post by croak77 on 2006-04-19
What qt package did you install? libqt3-mt?

---

### Post by kroiz on 2006-04-20
[quote=croak77]What qt package did you install? libqt3-mt?[/quote] 
I had libqt3-mt already installed.

I installed libQt3Support which which dragged installation of other qt 4 releated stuff.

and I'm still waiting to hear whether I should install libpng3.

---

### Post by kroiz on 2006-04-20
I installed libpng3 and tried again:
```
KeePassX: No Translation found for language 'English (UnitedStates)'
Qt: No Translation found for 'English (UnitedStates)'
keepass: symbol lookup error: keepass: undefined symbol: _ZN11QTreeWidget5eventEP6QEvent
```

I read somewhere that this is due to qt 4 and that I need a newer version- qt 4.1.2
It is not in the repositories. anyone know how I can upgrade qt?

---

### Post by croak77 on 2006-04-20
Didn't realize it was qt4. Maybe you should try an older version that uses qt3. Here's a link to an older version: [http://home.arcor.de/tareks/keepass-0.1.3/keepass_0.1.3_i386.deb](http://home.arcor.de/tareks/keepass-0.1.3/keepass_0.1.3_i386.deb)

---

### Post by kroiz on 2006-04-21
Thanks croak77, but I'm afraid I suffer from the "musthavelatest" disease. :)
did you install keepass?

besides I feel I'm getting close. I saw posts in google cache of ppls that had the same problem as me and got keepass to work by just upgrading qt. 
how hard can this be.

I guess I should just dare and build QT 4.1.2, and see what happens then.
but I am a little afraid from the lib subject. I'm afraid I'll make a mess.

I dont know why but for some reason my thread did not get much attention.
I thought that keepass is a popular program and the problems I got are simple?!
do I smell?;)

---

### Post by cwmccabe on 2006-04-21
[QUOTE=kroiz]
...I feel I'm getting close. I saw posts in google cache of ppls that had the same problem as me and got keepass to work by just upgrading qt. 
how hard can this be.[/QUOTE]

Were these posts on the same version of KeePass that you've installed?  With a previous version of KeePass I had a similar problem that was resolved by installing *libqt-mt.so.3*.

Currently I'm in the same boat as you, trying to install version 0.2.0 and running into the same problems you've described above.

---

### Post by croak77 on 2006-04-21
Did you see this:

KeePassX requires:
- X11
- Qt (Core,Gui,Qt3Support,Xml,Sql,Network) - (>= 4.0.0, I recommend to use 4.1.1 or later)
- libz (>= 1.2.1)
- libpng (>= 1.2.8 )
- libstdc++6 (>= 4.0.1)
- glibc (>=2.3.4) 

Also there was something about starting the script 'keepass.sh', not the keepass executable in the /bin directory.

---

### Post by kroiz on 2006-04-21
[quote=cwmccabe]Were these posts on the same version of KeePass that you've installed?  With a previous version of KeePass I had a similar problem that was resolved by installing *libqt-mt.so.3*.

Currently I'm in the same boat as you, trying to install version 0.2.0 and running into the same problems you've described above.[/quote] 
Thanks, nice knowing.
and yes they were refering to version 0.2

---

### Post by kroiz on 2006-04-21
[quote=croak77]Did you see this:

KeePassX requires:
- X11
- Qt (Core,Gui,Qt3Support,Xml,Sql,Network) - (>= 4.0.0, I recommend to use 4.1.1 or later)
- libz (>= 1.2.1)
- libpng (>= 1.2.8 )
- libstdc++6 (>= 4.0.1)
- glibc (>=2.3.4) 

Also there was something about starting the script 'keepass.sh', not the keepass executable in the /bin directory.[/quote]

Yep, but I could not find any keepass.sh on my computer.

I tried adding to my /etc/apt/sources.list the repository of debian unstable and then when I opened synaptic It let me update to qt4.1.2 but it required me to uninstall some packages like "ubuntu-minimal" so I did not proceed. 

I am still hoping some guru will come along and will have a clear simple explanation on how to upgrade qt.

---

### Post by kroiz on 2006-04-24
I did it :D.
upgrading to lib qt 4.1.2 solved it indeed.

to upgrade to qt 4.1.2 do the following:
```
[LIST]
[*]sudo apt-get install checkinstall
[*]sudo apt-get install auto-apt
[*]sudo apt-get install build-essential
[*]wget http://freshmeat.net/redir/qt/8673/url_tgz/qt-x11-opensource-src-4.1.2.tar.gz[/LIST]
``` extract *qt-x11-opensource-src-4.1.2.tar.gz* to /tmp and change to that directory.

```
[LIST=1]
[*]auto-apt run ./configure
[*]make
[*]sudo checkinstall[/LIST]
```update the environment variable LD_LIBRARY_PATH to include the directory [I]/usr/local/Trolltech/Qt-4.1.2/lib

[/I]I did not had this env variable, if you dont either (in the terminal: echo $LD_LIBRARY_PATH returns blank) then add the following line to .bash_profile:
[I]LD_LIBRARY_PATH=/usr/local/Trolltech/Qt-4.1.2/lib;export LD_LIBRARY_PATH

[/I]hope that helps.

---

### Post by cwmccabe on 2006-04-26
are you running breezy or dapper?  i'm on breezy and the repositories in my sources.list file don't seem to have *build-essentials*.

---

### Post by kroiz on 2006-04-26
[quote=cwmccabe]are you running breezy or dapper?  i'm on breezy and the repositories in my sources.list file don't seem to have *build-essentials*.[/quote] 
sorry, that is build-essential with out the 's' in the end.
I fixed the error in my previouse post.

---

### Post by rog123 on 2006-05-01
Got the same error that you ppl got so I tried the application bundle instead. Worked like charm so I just placed a shortcut in the toolbar, next to the clock and suff, pointing to the shellscript that was part of the download

---

### Post by kroiz on 2006-05-02
[quote=rog123]Got the same error that you ppl got so I tried the application bundle instead. Worked like charm so I just placed a shortcut in the toolbar, next to the clock and suff, pointing to the shellscript that was part of the download[/quote]

thanks rog123,
If so then I would recomand every body to do it your way.
I did it with the deb package because I was not aware of the "application bundle" because there was a week or two that the keepass linux site was offline.
and I did not realize it was a temporary thing.

---

### Post by darkarchon on 2006-05-02
just to let u know, there's application bundle:
"The application bundle is ideal for portable usage with memory sticks or if one wants to use KeePassX without touching the system by installing libraries. The bundle contains i386 Linux binary and nearly all needed libraries. The only external dependency is a X server with Xinerama, Xrandr extension and a standard C library."

if u use it, u dont need any additional packages on ur system

---

### Post by kroiz on 2006-05-02
where do you extract it to? /usr/bin?
I mean what is the standard place for programs?

---

### Post by darkarchon on 2006-05-02
as far as i can tell, there's no standard place for such standalone executables.
well there's /opt dir and in some guides ppl store such stuff there. personally, i created $HOME/progs dir and put my swiftfox and azureus there.
if u wanna make ur prog available from anywhere, u could put a symbolic link in /usr/bin.

---

