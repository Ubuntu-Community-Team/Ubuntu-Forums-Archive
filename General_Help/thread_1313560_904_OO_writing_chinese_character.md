---
title: "904 OO writing chinese character"
date: 2009-11-03
forum: General Help
---

### Post by flyingsliverfin on 2009-11-03
how do i write chinese characters? I want to enter the pinyin, then it will give me the choices where i select the character (i think thats the way word does it)

also, i happen to have been fooling around trying to get it to work myself, and i screwed some things up. How do i reset all of the defaults, or do i have to reinstall OO?

---

### Post by edin9 on 2009-11-03
> **flyingsliverfin said:**
> how do i write chinese characters? I want to enter the pinyin, then it will give me the choices where i select the character (i think thats the way word does it)

also, i happen to have been fooling around trying to get it to work myself, and i screwed some things up. How do i reset all of the defaults, or do i have to reinstall OO?

Do you mean OpenOffice?

---

### Post by wildweathel on 2009-11-03
System -> Administration -> Language Support -> Install/Remove 

Then, on Karmic at least, 
System -> Preferences -> IBus Preferences

I'm not sure if Jaunty uses IBus or SCIM.  See what's on the panel.

To reset your OO settings, run the command "rm -r ~/.openoffice.org" in a terminal.

I typed up a nice long post earlier but Firefox crashed.  Ask if you have any further questions.  Have fun.

---

### Post by flyingsliverfin on 2009-11-04
right.. i ran the command and there is no OO directory under root.. i havent created  a root user (i think i need to). Anyway, i found a .openoffice under my user (/home/name)... is this what i should delete?

oh yea, jaunty uses scim, whatever that is.

should have been more specific: i want this for OO. isnt there just  a plugin for OO that i can install to make me able to type chinese just in OO, and not make it the systemwide default?

---

### Post by flyingsliverfin on 2009-11-19
?

---

### Post by Irihapeti on 2009-11-19
Scim has to be installed system-wide. It can't be done for one package.

Scim and scim-bridge should be installed by default. If you've removed them while playing around, reinstall them. For pinyin, install scim-pinyin through Synaptic (System -> Administration -> Synaptic). There's no need to reinstall OpenOffice.

Open System -> Administration -> Language Support, and make sure that the box "Enable support to enter complex characters" is checked. 

The next step has to be done in a terminal. Open a terminal (Applications -> Accessories -> Terminal) and paste or enter the following command.

```
locale | grep 'LANG='
```
This will output something like ```
lang=en_US.UTF-8
```
The bit after the = is your system language. You will use this in the next step.

Now enter or paste
```
im-switch -z [your language] -s scim-bridge
```
Replace [your language] with the output you got from the previous command. On my system, it is
```
im-switch -z en_NZ.UTF-8 -s scim-bridge
```
Unless you are in NZ, yours will be different.

Log out and in again, start OpenOffice and scim should work when you press control-space. You will need to press shift-control a few times to get to the pinyin input.

---

### Post by flyingsliverfin on 2009-11-22
THANK YOU

no more fiddling around :D

---

### Post by Irihapeti on 2009-11-22
&#19981;&#23458;&#27668;&#12290;You're most welcome.

---

### Post by flyingsliverfin on 2009-11-22
&#19981;&#23458;&#27668;&#12290;...

just started learning chinese, but i recognize the first one, isnt it bu (no)?

---

### Post by Irihapeti on 2009-11-22
Yes it is. The whole sentence is "bú kè qi" in pinyin. It means something like "Dont' mention it." or "You're welcome."

I've not been learning Chinese for very long, either. It's an interesting language, though. I find that the Chinese people here in Auckland are very happy when someone tries to speak their language.

---

### Post by flyingsliverfin on 2009-11-24
San diego/Calif has not of chinese speaking people :) my friends are mostly east asian and comtinously make fun of me in chinese. (one of the reasons i decided to learn)

---

### Post by Irihapeti on 2009-11-24
Chinese is a useful language to know, anyway. As for your friends, maybe one day you can make fun of them as well... :)

Good luck.

---

### Post by flyingsliverfin on 2009-11-24
thx

---

