---
title: "substitute gedit for vim?"
date: 2012-05-27
forum: General Help
---

### Post by cmcanulty on 2012-05-27
I have a rather specific question about a series of commands. I got this particular fix to work already (making a 32 bit driver work for a 64 bit system). But my question involves how I can substitute gedit for vim in the future in this type of situation.On the lines below that starts with vim, instead of vim could I type sudo gedit or just gedit? I find vim very hard to use and I am more prone to screwing it up as I don't really understand it.

```
sudo apt-get install ia32-libs
sudo mkdir /usr/share/cups/model/
mkdir ~/scratch
mkdir ~/scratch/brother
cd ~/scratch/brother
wget http://www.brother.com/pub/bsc/linux/dlf/brhl2140lpr-2.0.2-1.i386.deb
wget http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2140-2.0.2-1.i386.deb
dpkg -x brhl2140lpr-2.0.2-1.i386.deb common
dpkg --control brhl2140lpr-2.0.2-1.i386.deb
vim DEBIAN/control #(remove the "Dependency: libc ..." line)
cp -a DEBIAN/ common/
dpkg -b common brhl2140lpr-2.0.2-1.i386.deb
sudo dpkg --force-all -i brhl2140lpr-2.0.2-1.i386.deb
rm -rf common/ DEBIAN/
dpkg -x cupswrapperHL2140-2.0.2-1.i386.deb common
dpkg --control cupswrapperHL2140-2.0.2-1.i386.deb
vim DEBIAN/control #(remove the "Dependency: libc ..." line)
cp -a DEBIAN/ common/
dpkg -b common/ cupswrapperHL2140-2.0.2-1.i386.deb
sudo dpkg --force-all -i cupswrapperHL2140-2.0.2-1.i386.deb
```

---

### Post by steeldriver on 2012-05-27
you should be able to replace plain 'vim' with plain 'gedit'

if the instructions require 'sudo vim' then you would probably want 'gksudo gedit' (in a gnome-based environment)

see [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

regards

---

### Post by listerdl on 2012-05-27
Ive never understood VIM either....

I only use basic HTML/5 CSS PHP and I think it is more for ruby people or python, perl - etc

Check out bluefish if you have basic files to edit..

---

### Post by cmcanulty on 2012-05-28
thanks, is there a way to make gedit the default so I never have to deal with vim. I don't get why it is better as is seems very hard to learn and gedit is a breeze.

---

### Post by codemaniac on 2012-05-28
Are these manual steps to be performed , or you want to scriptize the whole array of activities ?

---

### Post by dcstar on 2012-05-28
> **cmcanulty said:**
> I have a rather specific question about a series of commands. I got this particular fix to work already (making a 32 bit driver work for a 64 bit system). But my question involves how I can substitute gedit for vim in the future in this type of situation.
.........]

**vim** is designed for the Command Line shell, **gedit** will only run in a Gnome environment.

A good replacement for **vim** is to use **nano** if you are restricted to a terminal.

PS I discovered in the late 1980's that **"vi**" really stood for "**V**irtually **I**mpossible" to use. It may have been valuable when you only had a 75 Baud teletype connection but it should have been put to death decades ago.

---

### Post by wojox on 2012-05-28
You could always uninstall vim since it isn't installed by default. You or some other admin added it. :P

---

### Post by cmcanulty on 2012-05-28
no what I want to know about when I encounter a sequence of commands like that where vim is in the middle how can I do it without using vim and not mess up the sequence.
OK I found a nice package that makes vim easy it is cream. Now I just have to know how to set it so when I invoke vim it goes to cream instead

[http://www.linux-mag.com/id/6045/]("http://www.linux-mag.com/id/6045/")

---

### Post by mc4man on 2012-05-28
> **cmcanulty said:**
> no what I want to know about when I encounter a sequence of commands like that where vim is in the middle how can I do it without using vim and not mess up the sequence.

In your example in post 1 simply substitute gedit for vim. (2 places
All you where doing there was unpacking 2 .debs, editing the control file(s), then repackaging. In that  ex. this was done as a user so no need to use gksudo.

(if you have ocassion where you need to use a cli editor then as mentioned nano is pretty easy to use. Just make sure it's set as the default editor in update-alternatives

```
sudo update-alternatives --config editor
```
EX.
> :~$ sudo update-alternatives --config editor
[sudo] password for doug: 
There are 3 choices for the alternative editor (providing /usr/bin/editor).

  Selection    Path               Priority   Status
------------------------------------------------------------
* 0            /bin/nano           40        auto mode
  1            /bin/ed            -100       manual mode
  2            /bin/nano           40        manual mode
  3            /usr/bin/vim.tiny   10        manual mode

Press enter to keep the current choice[*], or type selection number: 


---

### Post by victor.zamanian on 2012-05-28
> **dcstar said:**
> PS I discovered in the late 1980's that **"vi**" really stood for "**V**irtually **I**mpossible" to use. It may have been valuable when you only had a 75 Baud teletype connection but it should have been put to death decades ago.

Others might want to call it "Virtually Indispensable," considering it can be very useful to us advanced users. Putting a project to death just because it's not useful to one particular person doesn't seem very nice, when others find it very useful. :-)

Personally, I like both vim and emacs, but in an ideal world, I'd like to mix and match features from both emacs and vim. :-\

---

### Post by codemaniac on 2012-05-28
> **cmcanulty said:**
> no what I want to know about when I encounter a sequence of commands like that where vim is in the middle how can I do it without using vim and not mess up the sequence.

Hi ,
If they are just sequential steps to be executed , then you can simply avoid vim and use other console based editors like nano as suggested above .If you used to have remote ssh sessions then using gedit wont be feasible .

---

### Post by cmcanulty on 2012-05-28
OK thanks

---

