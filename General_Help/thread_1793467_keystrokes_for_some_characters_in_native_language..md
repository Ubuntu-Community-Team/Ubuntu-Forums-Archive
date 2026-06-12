---
title: "keystrokes for some characters in native language."
date: 2011-06-29
forum: General Help
---

### Post by chinmay3 on 2011-06-29
i have installed a font known as 'kf-kiran' to type in my mothertounge. it is true type font compatible for xp, mac & linux distros. but there are some characters which i want to type but doesn't get using key combinations i used in xp. in character map it shows something like "U+00D1"(209) etc. . But i am unable to understand what this mean. can anybody tell me what is this & how to overcome this situation. thanks in advance.:confused:

---

### Post by Vaphell on 2011-06-29
if you want to type any unicode character knowing its code press ctrl+shift+u (_**u**_ shows up) then 00d1, space/enter
Ñ

isn't there a proper keyboard layout for your language to do that with simpler combinations?

---

### Post by chinmay3 on 2011-06-30
[SIZE=3]thanks for reply.
But it is quite irritating that 8 keystrokes for single character , isn't it?:(
[/SIZE]

---

### Post by Vaphell on 2011-07-01
that's why i asked about a proper keyboard layout for your language of choice that has some nice shortcuts in place.
also you can set up your own, google a bit for 'linux custom keyboard layout'

---

### Post by chinmay3 on 2011-07-01
But with same keyboard , in xp i am typing those characters by shortcut like " alt+012".
Then why it is so tedious with ubuntu. I am not comparing  ubuntu with xp but that is one good thing in xp inspite all other bad things.:)

---

### Post by Vaphell on 2011-07-04
1. add 2nd layout and switch between them - it doesn't hurt

2. read about compose key, it's a method of input that blows alt+whatever out of the water. You press compose key (you can configure which of special keys performs that function) and produce Ñ with N,~. Dig in keyboard layout preferences to set it up.
look at the table with the list of possible combos so you have an idea what you are missing ;-)
[http://www.hermit.org/Linux/ComposeKeys.html](http://www.hermit.org/Linux/ComposeKeys.html)

3. read about keyboard layout customization and add your own hand made layouts/combinations

Windows alt method is 'easier' because it doesn't deal with full unicode tables (only 0-255 codes) so combos are shorter. Downside is that win method is not future proof and you can't type any character possible while unicode codes allow for tens of thousands characters to by typed with no hassle given that you know the code. Besides, is holding alt to press 3 keys really easier than 3key press plus typing code normally? you get visual feedback you don't have with alt.

---

