---
title: "some symbols can not type in the terminal"
date: 2009-10-09
forum: General Help
---

### Post by tanyeun on 2009-10-09
hi all :D
I am using Hardy
I can not type some symbols(~ ^ ´ ¨) in my xterm terminal
I tried gnome terminal (¨ ´) still doesn´t work
but they works from on anywhere else like browser or word editor
anyone know how to fix it 

thx,

David

---

### Post by tanyeun on 2009-10-24
anyone help??

I think it&#347; bcs of the locale different
bcs I am native Chinese speaker
so I installed some of the lang packages
in order to view Chinese

and I use scim to type Chinese
I tried to change some setup on scim
then I can be able to type ~ and ^
but still can´t type ¨, ´ which is very important while programming
I can type ¨, ' in command line based text editors like vim
but the shell can´t recognize ¨, ´
it treats ¨, ´ as some other symbols which is not ascii

$ locale
LANG=en_US.UTF-8
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C

plz help
everytime I do some shell command et.
I have to copy paste ¨, ´, ^, ~
very inconvenient

---

### Post by Irihapeti on 2009-10-26
I think that the problem will be your locale settings.

If you have suitable Chinese fonts installed, you can read and type Chinese even if your locale is completely set to en_US.UTF-8 (or other English UTF-8 locale). Your other option would be to change completely to a Chinese locale, but that installs a large amount of extra software.

Go to System -> Administration -> Language Support and set your default language to English (US) and make sure that the box under "input method" is checked. You'll then need to reboot.

---

### Post by tanyeun on 2009-10-30
my default language is set to en_US, and the input method box is checked
the problem still remains

how do you installed the Chinese font properly??
the way I do is to installed the Chinese package in Language support

---

### Post by Irihapeti on 2009-10-31
I found some links on fixing locale errors in Ubuntu.

Check that the entry "en_US.UTF-8 UTF-8" appears in the files /var/lib/locales/supported.d/en and /var/lib/locales/supported.d/local
Add it if necessary.

Enter these commands in a terminal:

```
sudo locale-gen
```

then

```
sudo dpkg-reconfigure locales
```
References: [http://www.cyfinity.com/2009/01/fixing-locales-error-on-ubuntu/](http://www.cyfinity.com/2009/01/fixing-locales-error-on-ubuntu/)
[http://blog.bigsmoke.us/2009/06/16/adding-locales-in-ubuntu](http://blog.bigsmoke.us/2009/06/16/adding-locales-in-ubuntu)

The Chinese fonts were probably installed when you added the Chinese language support. They are in the repositories, under the names of ttf-arphic-uming, ttf-arphic-ukai and ttf-wqy-zenhei

There is a later version of ttf-wqy-zenhei available from the WenQuanYi SourceForge site.

I hope this helps.

---

### Post by tanyeun on 2009-10-31
thx for the tips on Chinese font :D
but I found out my problem is not about locale
it's about keyboard layout
[https://answers.launchpad.net/ubuntu/+source/gcc-defaults/+question/48341](https://answers.launchpad.net/ubuntu/+source/gcc-defaults/+question/48341)
I found someone have the same problem as I am
I tried to type double quote (")(unicode: \u0022 )
but instead it show up to be umlaut (¨) (unicode: \u00a8 )
Greg provide a solution is to press space bar after
but so far I still don't know how to make my keyboard back to normal
```
sudo dpkg-reconfigure -plow console-setup
```
this can allow keyboard change
but I don't know which one is the right one I should choose
I am using Thinkpad X61

---

### Post by Irihapeti on 2009-10-31
Sorry, I don't know much about keyboard layouts. Under System -> Preferences -> Keyboard, there are about 4 options for IBM Thinkpads. I can only suggest trying each one and seeing if any of them work for you.

I still suspect that something is not right with the locale settings. Enter this command and see what happens:

```
perl -e0
```
It doesn't actually do anything, but if there is a locale problem, perl will return an error message. If you get no output at all, then the locale settings are fine.

---

### Post by tanyeun on 2009-11-01
nothing happens
it means?

---

### Post by Irihapeti on 2009-11-01
If nothing happens, it means that your locale settings are OK. Perl is very fussy about locale settings.

I'm sorry, I don't know what else to suggest. Maybe asking a question on Launchpad might get a useful answer.

---

### Post by tanyeun on 2009-11-14
still appreciate your help
I actually find it interesting that I can type umlaut characters
but I know nothing about German language :P

---

### Post by Irihapeti on 2009-11-14
Maybe there is something odd about your keyboard layout choice. Perhaps you have the wrong layout, or a variant of a layout, selected.

Go to System -> Preferences -> Keyboard and click on the layouts tab.

Try adding a new layout: USA, variant "default". Click the button to make that your default layout.

If that works, you can then remove the old one.

---

### Post by tanyeun on 2009-11-14
my default Layout is 
  USA International(with dead keys)
and the keyboard model is 
  IBM ThinkPad 560Z/600/600E/A22E, Intl

---

### Post by Irihapeti on 2009-11-14
Try installing a USA keyboard layout, default version, and see what that does.

I've attached a screenshot.

I seem to remember reading somewhere that international with dead keys can cause some problems with Scim.

---

### Post by tanyeun on 2011-02-16
sorry for the late reply
after changing my layout to USA really solved the problem
thx a lot :D

---

### Post by tanyeun on 2011-03-08
additional notes
command line solution for this is
> $ setxkbmap us

---

