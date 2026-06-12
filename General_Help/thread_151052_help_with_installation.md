---
title: "help with installation"
date: 2006-03-27
forum: General Help
---

### Post by dotal on 2006-03-27
I'm struggling with the installation for quite some time.
now i have a new server installation.tried to install kubuntu desktop with apt-get but got cdrom error.
i was able to install the kde package with aptitude.
can i run the kde desktop now & if yes how?](*,) ](*,) ](*,)

---

### Post by adamkane on 2006-03-27
Log out, and select a KDE session at the login screen.

---

### Post by dotal on 2006-03-27
[QUOTE=adamkane]Log out, and select a KDE session at the login screen.[/QUOTE]
what is the command?

---

### Post by adamkane on 2006-03-27
Please give more details about your situation.

Are you stuck at the command line terminal? Do you get any kind of graphical display when you logon?

I was assuming you were still able to log in, but not into KDE.

---

### Post by dotal on 2006-03-27
[QUOTE=adamkane]Please give more details about your situation.

Are you stuck at the command line terminal? Do you get any kind of graphical display when you logon?

I was assuming you were still able to log in, but not into KDE.[/QUOTE]

yes.im stuck at the command line terminal.when I start my computer it loads  
into the server's login mode.I dont have any graphical display yet, well thats 
where im trying to get to.

---

### Post by dotal on 2006-03-28
any one can help ?

---

### Post by Sutekh on 2006-03-28
Which KDE package did you install, do you know if it installed the K display manager (kdm)?

Try
```
sudo /etc/init.d/kdm start
```
or ```
startx
```

---

### Post by dotal on 2006-03-29
[QUOTE=Sutekh]Which KDE package did you install, do you know if it installed the K display manager (kdm)?

Try
```
sudo /etc/init.d/kdm start
```
or ```
startx
```[/QUOTE]
tried to run sudo /etc/init.d/kdm start
and it says k manager is alredy running.so how do I activate the graphic display???

---

### Post by Sutekh on 2006-03-29
[QUOTE=dotal]tried to run sudo /etc/init.d/kdm start
and it says k manager is alredy running.so how do I activate the graphic display???[/QUOTE]
I'm not too sure whats happening, but don't give up yet.  I have some sugegstions that you can try, hopefully they will work or shed some light on your problem.  

I was kind of hoping you would get an error like
```
K Display Manager Starting                           [[COLOR="Red"]FAIL[/COLOR]]
```

If the display manager is apparently already running, could you try pressing Ctrl+Alt+F7 and describe what happens (if anything)?

You could also try restarting the display manager from the command line using
```
sudo /etc/init.d/kdm restart
```Does this have any effect?

Lastly you could you tell me what package you installed with aptitude?  Was it the kubuntu-desktop package or kde-core or something else?   You could also try re-installing or re-configuring the kdm package, in case there was a problem when it was installed
```
sudo apt-get install --reinstall kdm
```
and ```
sudo dpkg-reconfigure kdm
```

Fingers crossed.

---

### Post by dotal on 2006-03-29
[QUOTE=Sutekh]I'm not too sure whats happening, but don't give up yet.  I have some sugegstions that you can try, hopefully they will work or shed some light on your problem.  

I was kind of hoping you would get an error like
```
K Display Manager Starting                           [[COLOR="Red"]FAIL[/COLOR]]
```

If the display manager is apparently already running, could you try pressing Ctrl+Alt+F7 and describe what happens (if anything)?

You could also try restarting the display manager from the command line using
```
sudo /etc/init.d/kdm restart
```Does this have any effect?

Lastly you could you tell me what package you installed with aptitude?  Was it the kubuntu-desktop package or kde-core or something else?   You could also try re-installing or re-configuring the kdm package, in case there was a problem when it was installed
```
sudo apt-get install --reinstall kdm
```
and ```
sudo dpkg-reconfigure kdm
```

Fingers crossed.[/QUOTE]

1.Ctrl+Alt+F7 - no response
2.sudo /etc/init.d/kdm restart - it says kdm is stopping &kdm is on again & Im back to the prompt.
3.in aptitude i look at installed packages : kde - the kde desktop system (it was installed from the kubuntu insatallatin cd
4.sudo dpkg-reconfigure kdm - tried it without reinstall : it says reconfigured & back to the prompt.

---

### Post by dotal on 2006-04-02
success eventually - I didnt give up and found out the problem.
I didnt have the x package. installed that and got the kubuntu gui.:D

---

