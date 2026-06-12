---
title: "invalid argument"
date: 2010-06-19
forum: General Help
---

### Post by COKEDUDE on 2010-06-19
Could anyone explain why this is a invalid argument? I thought you were supposed to give a directory at the end of this. 

```
~ $ sudo grep "his" /home/bob
grep: /home/bob: Invalid argument
```

---

### Post by davidmohammed on 2010-06-19
what were you trying to achieve?

suggest remove the quotes and replace with a wild card for files if you want to find the text "his" in all files in a directory

i.e.

grep his /home/bob/*

---

### Post by COKEDUDE on 2010-06-21
> **davidmohammed said:**
> what were you trying to achieve?

suggest remove the quotes and replace with a wild card for files if you want to find the text "his" in all files in a directory

i.e.

grep his /home/bob/*

I was trying to search for the text string of "his" in files. Here are some examples of how I learned about this. 
[http://www.cyberciti.biz/faq/howto-search-find-file-for-text-string/](http://www.cyberciti.biz/faq/howto-search-find-file-for-text-string/)
[http://www.iceteks.com/articles.php/grep/1](http://www.iceteks.com/articles.php/grep/1)
[http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/](http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/)

---

### Post by COKEDUDE on 2010-06-24
Does anyone know why I get a invalid argument?

---

### Post by tgm4883 on 2010-06-24
This may sound dumb, but is /home/bob a valid file or directory?

It's odd, cause I get an invalid file or directory error when running that command. Maybe you should add a -R in there?

```
sudo grep -R his /home/thomas
```

---

### Post by COKEDUDE on 2010-06-24
> **tgm4883 said:**
> This may sound dumb, but is /home/bob a valid file or directory?

It's odd, cause I get an invalid file or directory error when running that command. Maybe you should add a -R in there?

```
sudo grep -R his /home/thomas
```

Yes it is valid :). It also works for me when I add the -R option. I just wanna search the current directory though. The -R option makes it search recursively though. I then get overwhelmed by the amount of information. I only wanna search the "/home/bob" directory. Do you know of any other filter commands that will ignore the rest of my directories? I'm not very good with filter commands.

---

### Post by tgm4883 on 2010-06-24
Try adding --directories=read instead of -R

---

### Post by COKEDUDE on 2010-06-28
No luck :(. 
```
sudo grep --directories=read "his" /home/bob
grep: /home/bob: Invalid argument

```

---

### Post by RJARRRPCGP on 2010-06-28
Don't "invalid argument" mean the same thing as an invalid parameter? 
Meaning you typed an invalid option?

---

### Post by tgm4883 on 2010-06-28
what is the output of the following commands


```
dpkg -l grep
```

```
which grep
```

```
lsb_release -a
```

---

### Post by oldos2er on 2010-06-28
Probably don't need sudo. Try ```
grep his* /home/bob/*
```

---

### Post by COKEDUDE on 2010-06-29
> **tgm4883 said:**
> what is the output of the following commands


```
dpkg -l grep
```

```
which grep
```

```
lsb_release -a
```

How does this look? I really wish I knew about the "which" and "lsb_release -a" commands a long time ago. I write scripts fairly often and it always a pain to find find the full paths of commands. I found the "lsb_release -a" command a few days ago :). 
```
~ $ dpkg -l grep
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  grep           2.5.4-4build1  GNU grep, egrep and fgrep
~ $ which grep
/bin/grep
~ $ lsb_release -a
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 9 Isadora
Release:	9
Codename:	isadora
```


I now understand the problem. Problem one is you can't search for a string inside of a directory. Problem two since this is the home directory there are a lot of hidden files. So you gotta use the proper syntax with wildcards to search through hidden files and regular files. This would be the command to search through both regular files and hidden files. 
```
grep "his" /home/bob/{.,[a-z],[A-Z]}*
```

This does not work. It searches for "a-z" and not the letters a through z. This will also search for "A-Z" and not the letters A through Z. 
```
grep "his" /home/bob/{.,a-z,A-Z}*
```

This does not work. This ignores "." so it does not search hidden files at all. 
```
grep "his" /home/bob/[.,a-z,A-Z]*
```

This does a decent job of explaining wildcards. 
[http://linux.about.com/od/lts_guide/a/gdelts66t00.htm](http://linux.about.com/od/lts_guide/a/gdelts66t00.htm)

---

### Post by bone2006 on 2010-08-10
grep searches through files and pulls out the string with the parameters you pass to it.

You passed a folder, which is why it's invalid

If you want it to search the entire directory, then put a * at the end of the folder /*

So if you want to grep the word his in any file in your home directory it would be

grep his /home/user*

You don't needa  * before or after the his nor quotes.   If you have a text with

asffasfsfsfhisasdfasfsdf or
this is his story 

it will still work, so * before or after the his isn't needed.

---

### Post by COKEDUDE on 2011-01-09
This suppresses some of the error messages **2>/dev/null**. I am not sure how to suppress all of the error messages. For example. 

The normal way. 

```
~ $ sudo grep -ri "screensavers" /etc/*
grep: /etc/alternatives/net: No such file or directory
grep: /etc/alternatives/net.8.gz: No such file or directory
grep: /etc/alternatives/nmblookup: No such file or directory
grep: /etc/alternatives/nmblookup.1.gz: No such file or directory
grep: /etc/alternatives/testparm: No such file or directory
grep: /etc/alternatives/testparm.1.gz: No such file or directory
grep: /etc/blkid.tab: No such file or directory
grep: /etc/nologin: No such file or directory
Binary file /etc/X11/X matches
/etc/xdg/menus/gnome-screensavers.menu:  <Name>Screensavers</Name>


```

With **2>/dev/null**. 

```
~ $ sudo grep -ri "screensavers" /etc/* 2>/dev/null

Binary file /etc/X11/X matches
/etc/xdg/menus/gnome-screensavers.menu:  <Name>Screensavers</Name>


```

---

