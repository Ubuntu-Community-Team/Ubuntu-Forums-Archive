---
title: "Other letters on English keyboard"
date: 2009-08-08
forum: General Help
---

### Post by zbigniew_boniek on 2009-08-08
Hello!

I have an English keyboard, but I would like to use so Hungarian letters that aren't in English language (á,é,í,ó,ö,&#337;,ú,ü,&#369;).
If I know well I have to use xmodmap, I have to create ~/Xmodmap file and it will load after login.
These are the key combinations that I want:

AltGr+a=á
Shift_L+AltGr+a=Á
AltGr+e=é
Shift_L+AltGr+e=É
AltGr+e=é
Shift_L+AltGr+e=É
AltGr+i=í
Shift_L+AltGr+i=Í
AltGr+o=ó
Shift_L+AltGr+o=Ó
AltGr+k=ö
Shift_L+AltGr+k=Ö
AltGr+l=&#337;
Shift_L+AltGr+l=&#336;
AltGr+u=ú
Shift_L+AltGr+u=Ú
AltGr+h=ü
Shift_L+AltGr+h=Ü
AltGr+j=&#369;
Shift_L+AltGr+j=&#368;

So could Anyone tell me what I have to write into the Xmodmap file to work my combinations?

---

### Post by CatKiller on 2009-08-08
> **zbigniew_boniek said:**
>  I have an English keyboard, but I would like to use so Hungarian letters that aren't in English language (á,é,í,ó,ö,&#337;,ú,ü,&#369;).
If I know well I have to use xmodmap,

Not necessarily. You could use your Compose key. For example, to put a ´ above a character, you would use, for example, Compose &#8594; ' &#8594; i to get í. Compose &#8594; = &#8594; o gets you &#337;, Compose &#8594; " &#8594; O gets you Ö, and so on.

---

### Post by Icebear on 2009-08-08
I change the keyboard by altering the xkb setup



go to X11/symbols diretory, 	by typing cd /usr/share/X11/xkb/symbols
then find layout you want to change

for example ru (for Russian)

make a backup of the selected file,	sudo cp ru ru_backup
then load the file up to edit,	sudo gedit ru

find the section you want in it to change 
in my case the phonetic layout

then swap changes you wish to make

for example: from
key	<LatV> {	[    Cyrillic_zhe,    Cyrillic_ZHE	]	};
to
key	<LatV> {	[    Cyrillic_ve,    Cyrillic_VE	]	};

If you want to add a  2nd letter to a key then at the spot where it describes the level

in the Russian phonetic spot change the level from ALPHABETIC to FOUR_LEVEL_ALPHABET or  FOUR_LEVEL

for example from
key.type[group1]="ALPHABETIC";
to
key.type[group1]="FOUR_LEVEL_ALPHABETIC";

and at the key add the letter you want to change after the first two settings.

You can use unicode numbers also instead of names. (Don't use the +  sighn  ie. U4C7)

from
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN	]	};
to
key	<LatN> {	[     Cyrillic_en,     Cyrillic_EN,	U04C8,		U4C7	]	};

then save

Then go System>preferences>Keyboard

then click layout options
then click the other options button
then choose third level choosers
and choose button you wish to use for the 2 
To get the 2 letter while typing hold down the 3rd level key plus the key you want to use and for capital hold shift as well

next time you log in it should work
It would be most likely best not to experiment on the default language until you tried your changes on a second language keyboard.

---

### Post by vancheese on 2009-09-11
Did this work? can you share your successful file?
I do generally use the method that CatKiller suggested but is there a way for adding the Hungarian umlaut? &#368; as I can only seem to make Ü using that method?

---

### Post by CatKiller on 2009-09-11
> **vancheese said:**
> is there a way for adding the Hungarian umlaut? &#368;

Compose &#8594; = &#8594; U gives you &#368;.

There's a table (I don't know if it's complete) [here]("http://www.hermit.org/Linux/ComposeKeys.html").

---

### Post by vancheese on 2009-09-17
Hmm the compose and =  key combination doesn't seem to work for me, whilst the rest do! 
Any thoughts?

---

### Post by StuartN on 2009-09-17
> **vancheese said:**
> Hmm the compose and =  key combination doesn't seem to work for me, whilst the rest do! 
Any thoughts?

Try compose double-quote (") for an umlaut, e.g. ö, and yes you must press shift-2 for the " which is a little awkward.

To see a map of your own keyboard you can go to System->Preferences->Keyboard->Layouts and then select "Print Layout Diagram" to get a print preview. You can also click the "+" to look at the layout for any alternative keyboard - I found I needed to expand the image to full screen width to actually read the legends.

---

### Post by niteshifter on 2009-09-17
> **zbigniew_boniek said:**
> Hello!

I have an English keyboard, but I would like to use so Hungarian letters that aren't in English language (á,é,í,ó,ö,&#337;,ú,ü,&#369;).


By English I take that to mean USA or United Kingdom layout.
The below may be easier (no editing - by you - of xmodmap needed).

Step one:

Click System -> Preferences -> Keyboard. A dialog titled Keyboard Preferences should appear.

Click the Layouts tab.  

You should see in the list "Selected Layouts":
USA (or United Kingdom)

Click the Add button. In the Layout chooser dialog that appears, click on "Layouts", scroll the list down to USA (or United Kingdom). Next click on "Variants" select "International (with dead keys)".

Click the the Add button to close the Layout Chooser dialog.

Click the "Default" button beside USA (or United Kingdom)/

Click Close to close the Keyboard Preferences dialog.

You now have two possible keyboard layouts you can use. Now let's make switching between them easy. We're going to add an applet to one of the GNOME panels.



Step two:

Right click on a panel (top or bottom).

Click "Add to Panel.

Scroll down the list, looking for "Keyboard Indicator". Click on it.

Click the Add button.

On the panel you should now see the text "USA" or "UK".



Using it:

Left click on the applet - the text changes from USA to USA2 (or UK to UK2). Since in this example we have just two layouts left-clicking just toggles us between normal and "dead keys". What dead keys means is some keys will appear to be dead (like the ' " key, for example.

To type á or Á: toggle to USA2/UK2. Press the ' key (nothing will appear), then press the a (or Shift + A) - you have the character with the diacritical mark.
To type ü, ö, Ü, Ö: toggle mode, press the Shift + ' (i.e. the "), followed by the character you wish to mark.

Expermiment a bit, it's easy to get the hang of it :)

---

### Post by vancheese on 2009-09-17
ö and ú aren't the problem! its getting the Hungarian umlaut([http://en.wikipedia.org/wiki/Double_acute_accent)&#337;,&#369;](http://en.wikipedia.org/wiki/Double_acute_accent)&#337;,&#369;) which should be the compose key + = but this mapping doesn't seem to work whilst I can do the other type by using the compose key.

---

### Post by StuartN on 2009-09-17
My (Irish) English keyboard layout does umlaut (ü) with compose-" and Hungarian umlaut (&#369;) with compose-=, as listed in the Linux compose key / Unicode list at [http://www.hermit.org/Linux/ComposeKeys.html](http://www.hermit.org/Linux/ComposeKeys.html)

---

### Post by niteshifter on 2009-09-17
> **vancheese said:**
> ö and ú aren't the problem! its getting the Hungarian umlaut([http://en.wikipedia.org/wiki/Double_acute_accent)&#337;,&#369;](http://en.wikipedia.org/wiki/Double_acute_accent)&#337;,&#369;) which should be the compose key + = but this mapping doesn't seem to work whilst I can do the other type by using the compose key.

Ah, now I see. Still what I wrote will work - just set the alternate mapping as Hungarian rather than international w/ dead keys. Still no need to fool around with xmodmap.

I just added Hungararian to mine, the \| key now gives &#369; &#368;.

```
USA Shifted numerals: ! @ # $ % ^ & * ( ) _ +
Hungarian             ' " + ! % / = ( ) Ö Ü Ó

USA: qwertyuiop[]\  QWERTYUIOP{}|
Hun: qwertzuiop&#337;ú&#369;  QWERTZUIOP&#336;Ú&#368;

USA: asdfghjkl;'  ASDFGHJKL:"
Hun: asdfghjkléá  ASDFGHJKLÉÁ

USA: zxcvbnm,./  ZXCVBNM<>?
Hun: yxcvbnm,.-  YXCVBNM?:_

```

Does that work for you?

---

