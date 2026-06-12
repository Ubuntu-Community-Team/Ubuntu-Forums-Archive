---
title: "Problem with setting up Kile under ubuntu"
date: 2006-03-29
forum: General Help
---

### Post by oldnumber7 on 2006-03-29
Hi, here is a new user of ubuntu
I used 'synaptic package manager' to install Kile. It's no problem to compile the latex file to get dvi file and ps file. But when I click the preview dvi button or viewps button. The wrong message appeared: [ViewDVI] Could not find the kviewerpart library.

Did I miss installing something? How to deal with this? Thanks.

Vol.

---

### Post by neoflight on 2006-03-29
[QUOTE=oldnumber7]Hi, here is a new user of ubuntu
I used 'synaptic package manager' to install Kile. It's no problem to compile the latex file to get dvi file and ps file. But when I click the preview dvi button or viewps button. The wrong message appeared: [ViewDVI] Could not find the kviewerpart library.

Did I miss installing something? How to deal with this? Thanks.

Vol.[/QUOTE]

try the one from my signature....

---

### Post by Barrakketh on 2006-03-29
This is from the kile-dev list:

> On Tuesday 28 June 2005 22:08, [email]jflores@usd.edu[/email] wrote:
> I have problems with Kile, I keep getting the following message. I do not
> know how to fix it, I have reinstalled KILE and it does not work so far.
>
> " [ViewDVI] Could not find the kviewerpart library"
>
> I new at Linux and KDE, any help to resolve this problem is welcome.
>

Hi,

This error message is telling you that the appropriate software, needed to run 
the dvi viewer, is not installed. The DVI viewer is called KDVI, the 
kviewerpart is a generic viewer, KDVI needs.

So, in short, you need to install KDVI. On SuSE this is part of the 
kdegraphics-tex library. It is completely independent from Kile.

best,
Jeroen

Ubuntu should've installed the KPart for it, but you could try re-installing kdvi (sudo apt-get --reinstall install kdvi).

---

