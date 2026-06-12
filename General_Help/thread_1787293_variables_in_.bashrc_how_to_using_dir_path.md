---
title: "variables in .bashrc: how to using dir path"
date: 2011-06-20
forum: General Help
---

### Post by thaitang on 2011-06-20
Hi,

I have what I hope is a fairly simple question to answer. In my ~/.bashrc file I can create this alias:
```
alias uChmodDP='chmod -R $1 $2' #specify permissions
```and the variables work fine. But I cannot seem to get any love from this alias:
```
alias umnt='umount /dev/$1'
```I realize the likely problem is the variable following hot on the heels of a specific directory, but is there anyway to specify a variable in an alias like this?

For some reason I cannot umount usb pen drives by right clicking, and have to always resort to the terminal to do so, which for me is no real biggie, but if I could create this alias it would be an even better no biggie to umount using the terminal.

Actually, the inability to right click to umount usb devices seems to be a Thunar issue since I run xubuntu. Using Nautilus I am able to right click and eject/safely remove devices. Using Thunar however, right click unmount always pukes back an error that the device must have been mounted on the command line or some such BS. But like I said it is no real biggie to use terminal, but an alias would be even nicer.

I prefer using Thunar and Xubu most of the time b/c my laptop is quite underpowered. 

cheers,
tt

---

### Post by Slim Odds on 2011-06-20
Read up on how bash uses single quotes and double quotes

---

### Post by nothingspecial on 2011-06-21
To use variables use functions in your .bashrc

eg

```
function blah () {
         blah blag -x -y -z; complicated commands; including \
         one "$1"; or more variables "$2"; blah blah
                 }
```

In this form, it is more or less the same as an alias, blah will execute the stuff in between the curly brackets.

---

### Post by Slim Odds on 2011-06-21
On further review, $1 etc. are not appropriate for use by an alias.

aliases are a little different than functions, etc.

Here is an example:
$ alias tryme='echo 1=$1 2=$2'
$ tryme 1 2
1= 2= 1 2

I would highly recommend the Advanced Bash Scripting Guide (I know that it has some issues, some people will mention these). Even the man page is very helpful.

---

