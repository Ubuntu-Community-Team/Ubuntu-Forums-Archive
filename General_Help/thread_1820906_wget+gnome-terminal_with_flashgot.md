---
title: "wget+gnome-terminal with flashgot"
date: 2011-08-08
forum: General Help
---

### Post by mr.akik on 2011-08-08
I am running ubuntu linux.
I use flashgot add-on with firefox.
When I download a file , I choose wget with the help of flashgot.
When flashgot starts download with wget ,xterm opens and the download
starts.So I can't copy the download link.
With lxterminal , gnome-terminal or rox-term it's possible to copy 
the download link but xterm has poor quality and it's not possible to
copy anything from it.
So, please tell me how I can use lxteminal or gnome-terminal with flashgot to 
download a file so that I can copy the download link.

---

### Post by blueridgedog on 2011-08-08
Have you considered renaming your xterm application binary to something else (as a backup), then creating a symbolic link to a terminal application that you prefer?  Not certain of the side effects, it is easy to undo if you find it not working to your satisfaction.

---

### Post by mr.akik on 2011-08-08
> **blueridgedog said:**
> Have you considered renaming your xterm application binary to something else (as a backup), then creating a symbolic link to a terminal application that you prefer?  Not certain of the side effects, it is easy to undo if you find it not working to your satisfaction.
I can't properly understand  what u r telling me to do.
But I renamed lxterminal to xterm from /usr/bin.
It didn't work. Then I removed xterm and renamed lxterminal to xterm.
It also failed to work.Then I added this line to /etc/bashrc:
alias xterm="lxterminal"
But nothing works.

---

### Post by fdrake on 2011-08-09
> **mr.akik said:**
> I can't properly understand  what u r telling me to do.
But I renamed lxterminal to xterm from /usr/bin.
It didn't work. Then I removed xterm and renamed lxterminal to xterm.
It also failed to work.Then I added this line to /etc/bashrc:
alias xterm="lxterminal"
But nothing works.

you may need to logout and login..
also i think changing the env var name would be easier and faster:

```
TERM=lxterminal
```
with no relogin required

---

### Post by mr.akik on 2011-08-09
> **fdrake said:**
> you may need to logout and login..
also i think changing the env var name would be easier and faster:

```
TERM=lxterminal
```with no relogin requiredI tried everything but nothing works.

---

### Post by mr.akik on 2011-08-10
can anyone help??

---

