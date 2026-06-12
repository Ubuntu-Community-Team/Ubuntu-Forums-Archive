---
title: "Azureus +Guarddog + Kubuntu"
date: 2006-04-30
forum: General Help
---

### Post by Myndmelder on 2006-04-30
Out of boredom I decided to dump ubuntu, and install kubuntu (no, my computer doesn't get much more use than for me to play with it).

The install was fine and I do prefer kubuntu to ubuntu.

But I am running into a snag, I decided not to use Automatix, nor Automatiks, and install all my software myself...

I got around to installing Azureus and tried to put it to work downloading some sartuday morning cartoons... Azureus is technically running fine, but it was firewalled.
So, I downloaded Guarddog and used it to shutdown the firewall (I am aware that this isn't smart, but I m trying to get Azureus working then I will configure Guarddog).

The problem I am having is that Azureus isn't DL anything...

I am getting either "everything is ok" (but nothing is downloading) [demonoid]
or,  "protocol exception" (not sure what that means) [digital distractions]

When I was on ubuntu I did not have this problem, and I did have firestarter configured.
If anyone has any advice it would be greatly apreciated.

Oh, and before I forget, I tried using ktorrent and I was having the same problem (that and I have been using azureus for so long I want to keep using it).

Cheers.

---

### Post by Myndmelder on 2006-04-30
Well, I managed to figure out that I am using and older version of Java and that is most likely creating the problem...

I have installed the latest java based on info in the forums, but azureus still wants to use the old one...

Help?!?

---

### Post by gingermark on 2006-04-30
You could download the new Azeureus from the website - it's available to a Linux binary that just runs - you don't need to install it.

You'd have to check the requirements, but that version might be more open to a newer version of Java,

---

### Post by byen on 2006-04-30
[QUOTE=gingermark]You could download the new Azeureus from the website - it's available to a Linux binary that just runs - you don't need to install it.
You'd have to check the requirements, but that version might be more open to a newer version of Java,[/QUOTE]
Hey myndmelder,
If I am not wrong I think the latest version of Azereus does infact need the new version of Java. Since you say that you have already installed the new version of Java... why not just try what gingermark has suggested. Im pretty sure you might be able to get it to work. If not let us know!
Goodluck!
~byen

---

### Post by MartinG on 2006-04-30
[QUOTE=Myndmelder]Well, I managed to figure out that I am using and older version of Java and that is most likely creating the problem...

I have installed the latest java based on info in the forums, but azureus still wants to use the old one...

Help?!?[/QUOTE]When you say the latest java, I hope that means Sun, as Azureus still won't run with the gnu version.  And did you run update-alternatives after installing? I suspect not if Azureus is still trying to use the old one.

run ```
update-alternatives --list java
``` to see what versions you have, then ```
sudo update-alternatives --set java <path>
``` to point your apps to the one you want.

---

### Post by Myndmelder on 2006-04-30
Bingo!!!

Thank you MartinG!!!

It is working fine now. All I have left to do is setup GuardDog to allow the port I am using and I'm in business.

---

