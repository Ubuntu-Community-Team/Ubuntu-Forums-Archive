---
title: "about XAMPP"
date: 2010-10-16
forum: General Help
---

### Post by rupeshsasne on 2010-10-16
Hello..
i am new to linux. and i am doing some php over here.. for that i am using XAMPP... but i am not able to start the panel of xampp..
i have installed gtk to but its not working.. i got following error message whenever i want to start the panel of xampp..


root@TUX:/opt/lampp# sudo /opt/lampp/lampp panel
python: /opt/lampp/lib/libz.so.1: no version information available (required by python)
python: /opt/lampp/lib/libcrypto.so.0.9.8: no version information available (required by python)
python: /opt/lampp/lib/libssl.so.0.9.8: no version information available (required by python)
Traceback (most recent call last):
  File "xampp-control-panel.py", line 18, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/libfontconfig.so.1: undefined symbol: FT_Select_Size

does any one having solution for this please help me...

---

### Post by gandaran on 2010-10-16
do you mean run the start panel?
for this just make a desktop or menu launcher, right click the desktop area and choose create launcher and fill in the start command with
```
gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
```
then just click the launcher to start the panel.

---

### Post by rupeshsasne on 2010-10-17
Thanx it is working...

cheers,
RUPESH

---

### Post by rupeshsasne on 2010-10-17
Here I am again.. :)
how do i get the UI panel of mysql from xampp...
i have mysql installed.. already... do i need to remove it completely...?

---

### Post by BadboyXD on 2010-10-20
[COLOR="Blue"]I really have no idea how to use the xampp to test out my webpages and php code, I figured I would use it just like the windows version. Just put my files into the htdocs so I can run and check how things work locally. But that doesn't seem to work for me, I can't make any changes in there. The xampp documentation isn't helpful at all cause there's nothing about it in there. Anyone able to give me a headsup on this?[/COLOR]

---

### Post by rupeshsasne on 2010-10-22
> **BadboyXD said:**
> [COLOR=blue]I really have no idea how to use the xampp to test out my webpages and php code, I figured I would use it just like the windows version. Just put my files into the htdocs so I can run and check how things work locally. But that doesn't seem to work for me, I can't make any changes in there. The xampp documentation isn't helpful at all cause there's nothing about it in there. Anyone able to give me a headsup on this?[/COLOR]
 
you need to download the xampp for linux... then unzip it under /opt directory..
once you have done it.. start the xampp by
sudo /opt/lampp/lampp start (for starting xampp)
and sudo /opt/lampp/lampp stop (for terminating)
 
now after this open your browser(any gnome desktop i dont know if it is working for KDE or not)
type the url [http://localhost](http://localhost)
then you will get the home page of your xammp
 
deploy your pages under htdocs which is the root directory for xampp...
you can also make a directory under htdocs like what i have done...
htdocs/php...  i am doploying my php pages under this php directory...
 
now the question is how i am accessing those
simple..
[http://localhost/php/mypage.php](http://localhost/php/mypage.php)
 
cheers,
rupesh

---

### Post by BadboyXD on 2010-10-25
[COLOR="Blue"]Yeah I installed it alright ad got everything running,I  just can't make any adjustments to th htdocs, I can't put my webpages in to test them out. I don't know how to do it via comandline if thats he way I have to do it.[/COLOR]

---

### Post by katykat on 2010-10-25
> **BadboyXD said:**
> [COLOR=Blue]Yeah I installed it alright ad got everything running,I  just can't make any adjustments to th htdocs, I can't put my webpages in to test them out. I don't know how to do it via comandline if thats he way I have to do it.[/COLOR]


Use mc (Midnight Commander) or gnome-commander to copy and move files anywhere. 
Make sure to go into Options and ensure that hidden files are visible.

---

### Post by BadboyXD on 2010-11-04
[COLOR="Blue"]Alright I'll try that, thanks for the help guys. Seems thats the best way to go lol. Thanks again all.[/COLOR]

---

