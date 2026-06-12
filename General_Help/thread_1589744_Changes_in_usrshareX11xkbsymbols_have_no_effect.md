---
title: "Changes in /usr/share/X11/xkb/symbols/* have no effect"
date: 2010-10-06
forum: General Help
---

### Post by ellbur on 2010-10-06
EDIT:

I have (sort of) found a solution.

There appear to be *.xkm files in /var/lib/xkb. According to 'man setkxbmap':

"An XKB keymap is constructed from a number of components which are  compiled  only  as  needed. The source for all of the components can be found in /usr/share/X11/xkb"

Deleting all of these files caused them to be recompiled. I would think there is a better way to do this, but this worked well enough for me.

CAUTION before you try this: it caused my keyboard to become Entirely Unusable in X next time it was started (but only that once).

----

I have a custom keyboard layout defined in /usr/share/X11/xkb/symbols/owen . I don't change it very often so I don't generally notice whether changing the file has any effect. However today I made some changes, rebooted, and found that they did not take effect.

Puzzled, I tried the "redo everything" strategy. I opened up KDE's keyboard config tool to remove and add "owen" from the layout list. After removing it I discovered it was not there to add. This turned out to be because the entry had been removed (probably during package upgrade) from /usr/share/X11/xkb/rules/evdev.xml. I added it back:
...
    <layout>
      <configItem>
        <name>owen</name>
        <shortDescription>Owen</shortDescription>
        <description>Owen</description>
        <languageList><iso639Id>us</iso639Id></languageList>
      </configItem>
      <variantList/>
    </layout>
...

And then KDE realized the layout existed. But it still behaved the same.

So then I tried deleting /usr/share/X11/xkb/symbols/owen and then rebooting, and sure enough, layout still present, and still exactly like it was before.

So I tried grepping for a distinctive phrase in the file, thinking maybe xkb had copied it somewhere secret:
21:29:13 /usr/share/X11 $ grep -r 'Owen' .
./xkb/rules/xorg.xml:        <shortDescription>Owen</shortDescription>
./xkb/rules/xorg.xml:        <description>Owen</description>
./xkb/rules/evdev.xml:        <shortDescription>Owen</shortDescription>
./xkb/rules/evdev.xml:        <description>Owen</description>
./xkb/rules/xfree86.xml:        <shortDescription>Owen</shortDescription>
./xkb/rules/xfree86.xml:        <description>Owen</description>
./xkb/rules/base.xml:        <shortDescription>Owen</shortDescription>
./xkb/rules/base.xml:        <description>Owen</description>
./xkb/symbols/steve:name[Group1]= "Owen";

('steve' is where I moved 'owen' to, so I didn't lose it).

Still, no luck.

Other things that might be relevant, but I'm not sure:

I use ckbcomp to use the same layout at the console. The console also uses the old layout with no changes.

I have a line in /etc/default/console-setup to use my layout at the console and the login screen:
XKBMODEL="pc105"
XKBLAYOUT="owen"

---

### Post by simosx on 2010-10-08
tl;dr. See [http://simos.info/blog/archives/1134](http://simos.info/blog/archives/1134) for example of adding a new keyboard layout.

---

### Post by ellbur on 2010-10-09
Simosx,

Thank you for your reply. That is a nice tutorial (I wish I'd had it back when I started playing around with keyboard layouts). However it seems to me that I have followed the same steps you describe, and it was working perfectly until just recently. In fact it still works other than that changes to the symbols file have no effect.

Best,
Owen

---

### Post by chip616 on 2011-02-24
ellbur:

> Deleting all of these files caused them to be recompiled. I would think there is a better way to do this, but this worked well enough for me.

Which files?  The *.xkm files in /var/lib/xkb, or the keyboard definition files in /usr/share/X11/xkb/symbols?

I moved (rather than deleted) the *.xkm files in /var/lib/xkb and rebooted.  No change for me, though two new *.xkm files were created on boot.

I have a custom keyboard for a foreign language that I created and used in Kubuntu 8.04.  I moved that file to /usr/share/X11/xkb/symbols and then hand edited /usr/share/X11/xkb/rules/base.lst to add my keyboard file to the list.  No matter what I do, the new keyboard definition file does not show up in Control Center | Regional and Language | Keyboard Layout | Layout.  This means that I cannot choose it, therefore I cannot use it.

There must be a way to refresh the list of available keyboard definition files, but I have not yet found it.

Anyone have a solution?

Frank.

---

### Post by ellbur on 2011-02-24
> **chip616 said:**
> Which files?  The *.xkm files in /var/lib/xkb, or the keyboard definition files in /usr/share/X11/xkb/symbols?


The *.xkm files in /var/lib/xkb

> 

I moved (rather than deleted) the *.xkm files in /var/lib/xkb and rebooted.  No change for me, though two new *.xkm files were created on boot.

I have a custom keyboard for a foreign language that I created and used in Kubuntu 8.04.  I moved that file to /usr/share/X11/xkb/symbols and then hand edited /usr/share/X11/xkb/rules/base.lst to add my keyboard file to the list.  No matter what I do, the new keyboard definition file does not show up in Control Center | Regional and Language | Keyboard Layout | Layout.  This means that I cannot choose it, therefore I cannot use it.
There are two (redundant) lists of keyboard layouts in /usr/share/X11/xkb/rules . There are the *.lst files that you mentioned, and there are the *.xml files. As far as I can tell Gnome's keyboard layout gui looks at one of the xml files. If you `ls -l `, you will see that most (but not all) are symlinks of each other -- they may as well all be symlinks of each other, since they all contain the same information (I think Gnome looks at evdev.xml, but I am not positive).

You can copy-paste one of the other keyboard layout entries in the file and modify it to match your own. Then it should show up in Control Center | Regional and Language | Keyboard Layout | Layout (maybe log out and log in again first).

If you want the keyboard layout to apply at login, you will need to specify it in /etc/default/console-setup in the lines (near bottom of file):

```
XKBMODEL="pc105"
XKBLAYOUT="yourlayout"
XKBVARIANT=""
XKBOPTIONS=""
```Hope this helps :-)

---

### Post by chip616 on 2011-02-26
Ellbur

Thanks for the help.  Deleting the *.xkm files does force a recompile, and this solved my immediate problem for me.

I took the US keyboard defintion file, and modified the US_intl variant to reflect what I needed.  I just cut the portion I needed out of my previous custom keyboard file, and pasted it into the US keyboard file in the US_intl section, replacing what was there before.  When I rebooted, there was no change, as you had noted originally.  I then deleted the *.xkm files and rebooted.  This time, when I selected the US_intl variant, my special keys were there.  The only issue now is that I have no way of seeing (other than typing) which of the two keyboards are selected, as the US keyboard flag in the kicker does not change its appearance if I use the variant.

In poking around on the Internet, I found this link:

[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)

Part way down on that page you will see a heading:

X11/xkb/rules/evdev.xml (&#8805; Ubuntu 8.10)

It appears that there was a chage to Xorg at this point.  Now one has to edit the file 

usr/share/X11/xkb/rules/evdev.xml

Editing the base.lst file no longer has any effect.  I'm sure that this is a bug, but getting it fixed will take a while for the developers to 1) see the need and 2) actually do it.  :)

One has to insert a reference to the newly added keyboard definition file in evdev.xml directly in order for it to show up in Control Center | Regional and Language | Keyboard Layout | Layout. I did that, and my previously created custom keyboard file now does appear, but it is broken somehow.  It shows up at Control Center | Regional and Language | Keyboard Layout | Layout, and I can select it, but I am unable to select the variant that I need in that file.

In any case, following your information, I have successfully modified an existing keyboard definition file to do what I need, and that is the important thing for me.  The rest of it can wait till I have more time.

Thanks for your help!

Frank.

---

### Post by Marzata on 2012-04-28
Is there any other way to compile (generate) new keyboard layouts instead to delete the old *.xkm files in /var/lib/xkb?

---

