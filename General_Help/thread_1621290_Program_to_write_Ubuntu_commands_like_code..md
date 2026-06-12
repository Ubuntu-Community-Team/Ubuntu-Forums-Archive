---
title: "Program to write Ubuntu commands like code."
date: 2010-11-14
forum: General Help
---

### Post by foxsick on 2010-11-14
I'm a noob in Ubuntu. I need the program which will help me to learn different ubuntu commands. I often forget them and after reinstall I don't want to search them in Google. Now I write them in the standard text editor and my code looks like this:


[I]Restore MBR:
Delete GRUB (fixmbr)
Ubuntu terminal then:
sudo apt-get install ms-sys
sudo fdisk -l
sudo ms-sys -m /dev/sda
WinXP LiveCD:
fixboot
fixmbr[/I]


But I want it looks like this:
[B]Restore MBR:
Delete GRUB (fixmbr)
Ubuntu terminal then:[/B]
```
sudo apt-get install ms-sys
sudo fdisk -l
sudo ms-sys -m /dev/sda
```
**WinXP LiveCD:**
```
fixboot
fixmbr
```
Is there any program to do this? :confused:

---

### Post by sohlinux on 2010-11-14
use an html editor like seamonkey composer and use tables to make the boxes for the code

---

### Post by lykeion on 2010-11-14
Here's an example of html/css you could use.
Note the *display:table* property might not work in IE but who uses that browser anyway ;)
[HTML]<html>
<head>
<style type="text/css">
p { 
	font: normal bold .9em sans;
	line-height: .5em;
}
pre {
	font-family: monospace;
	margin-left: 3em;
}
.code { 
	border: 1px solid black;
	padding: 1em;
	display: table;
}
  
</style>
</head>

<body>
<p>Restore MBR:</p>
<p>Delete GRUB (fixmbr)</p>
<p>Ubuntu terminal then:</p>
<pre>
Code:
<div class="code">sudo apt-get install ms-sys
sudo fdisk -l
sudo ms-sys -m /dev/sda
</div>
</pre>

</body>
</html>[/HTML]

---

