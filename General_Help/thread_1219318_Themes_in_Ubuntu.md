---
title: "Themes in Ubuntu"
date: 2009-07-21
forum: General Help
---

### Post by lynx93 on 2009-07-21
Hello!

I am a new ubuntu user and dont understand few things jet. So, I found very cool themes but it changed only colour for me and I dont het that stuff at the bottom with icons (like on MAC)

What should I do?

---

### Post by mudcat on 2009-07-21
the stock themes change only color; if it's a theme that you downloaded from the web you need to install it. If you are looking for the "Mac" dock; i suggest you take a look at Awn window manager. If the mac theme is what your going for, check out Mac4Lin.

---

### Post by GoldenSun on 2009-07-21
you should download emerald for more advanced themes.
Also just bing "ubuntu docks" for some options there.

---

### Post by devildoc5 on 2009-07-21
ok that "cool things with icons on the bottom" is a "dock" there are many options available for this cairo-dock, AWN has a dock, and a few others.  You must install these to have that, and then you can add "launchers" (kinda like shortcuts) and customize the icon of each one.  To install cairo-dock got to Add/Remove and in the upper right corner type in "cairo" it should bring up an option that has "Cairo Dock" then you would click that and choose apply.  It will install and then you can start using cairo-dock from then on.

If you like cairo-dock you can add it to your startup list by going to System>Preferences>Startup Applications click on "Add" and where it says command type in "cairo-dock" (without the quotes) add a name in the name field so you know what it is and you are as good as gold.

---

### Post by devildoc5 on 2009-07-21
> **GoldenSun said:**
> you should download emerald for more advanced themes.
Also just bing "ubuntu docks" for some options there.

I never knew "bing" had made it into the official terminology as of yet.....

so instead of telling someone to "google" something can we all just start telling them to "bingle" it?

---

### Post by s.fox on 2009-07-21
[FONT=Arial]Hi,

If you would like themes you could try [here]("http://www.gnome-look.org/").   

Then go:

[/FONT][FONT=Arial][B]System->Preferences->Theme.

[/B] You should be able to install the downloaded theme from there.

-Silver Fox[/FONT]

---

### Post by GoldenSun on 2009-07-21
> **devildoc5 said:**
> I never knew "bing" had made it into the official terminology as of yet.....

so instead of telling someone to "google" something can we all just start telling them to "bingle" it?

I was trying to start a new fad...

but I like your idea of "bingle"
like search both.

---

### Post by jerrrys on 2009-07-21
[http://bingle.pwnij.com/](http://bingle.pwnij.com/)

---

### Post by Codix121 on 2009-07-21
Here is the easiest way:

1. Open Up Your Terminal (Applications -> Accessories -> Terminal

Type in:

```
sudo apt-get install emerald libemeraldengine0
```

hit enter.

2. Upon Completion go to SYSTEM -> PREFERENCES -> EMERALD THEME MANAGER.

3. Go here: [http://www.gnome-look.org/content/show.php/Mac4Lin+Leopard+Emerald+Theme?content=68409]("http://www.gnome-look.org/content/show.php/Mac4Lin+Leopard+Emerald+Theme?content=68409")
Download the file it should be in .emerald format.

4. In EMERALD THEME MANAGER hit "IMPORT"and direct it to the .Emerald file. 

5. and then select the theme you just imported and close Emerald Manager.

6. hit ALT+F2 and type in 
```
emerald --replace
```

and your window should appear like a mac.
for more icons, etc... check out this page:

[http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23](http://maketecheasier.com/turn-your-ubuntu-hardy-to-mac-osx-leopard/2008/07/23)

There's a file called MODIFIED MAC THEME,
and inside that file there are tons of icons,
themes, etc that you can use.

----------------
EDIT:

To install the "DOCK" that looks like mac,
You have two options AWN (AVANT WINDOWS NAVIGATOR)
Or Cairo-Dock, in my opinion Cairo-Dock is more customizable,
and it just fits better with the "MAC" look.

To install that Open up TERMINAL again (APPLICATIONS ->ACCESSORIES ->TERMINAL

and type:

```
gksu gedit /etc/apt/sources.list
```
A document file should come up.
At the bottom of that file copy and paste this in there:

```
deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock
```
click SAVE and then close it,

Now in terminal type this:

```
wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
```
HIT ENTER.

Then after in terminal type this also:

```
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plugins
```

and it should install.
Then go to APPLICATIONS -> SYSTEM TOOLS -> CAIRO-DOCK NO GL. or WITH GL whichever one works for you,
Usually it's NO GL.

Now right click on the DOCK when it opens and select
MANAGE THEMES.

There is already a theme called MACOSX,
Select it and hit APPLY.

and now you have a dock!
Make sure you remove the original UBUNTU PANEL,
Right click on the panel and select DELETE THIS PANEL.

And now you have a pretty little dock :)



if you need more help, feel free to e-mail me, Some of it can get very confusing and I have some good resources to help pimp out your desktop with awesome eyecandy:

[email]jjaramillo661@gmail.com[/email]

I have attached a screenshot of my desktop so you can take a look:

---

### Post by devildoc5 on 2009-07-21
> **jerrrys said:**
> [http://bingle.pwnij.com/](http://bingle.pwnij.com/)

WOW.....Just....Wow......

Cairo dock is pretty easy to customize and you can always use our greatest friend The GIMP to make your own images for cairo-dock and have everything EXACTLY the way you want it.

---

### Post by Tipped OuT on 2009-07-21
Why is everyone showing him Mac OS X themes?


Anyways, go to: [http://www.gnome-look.org/](http://www.gnome-look.org/)

Go to the "Icons" section for icons, go to the "GTK 2.X" section for themes and etc.

To install them, just drag and drop the file or folder in the "Appearance" window. (System< Preferences< Appearance)

Simple as that.

---

### Post by Codix121 on 2009-07-21
It just seemed he was interested in a MAC like theme,
he obviously liked the dock,
either way, he can use emerald manager to install any other Emerald
theme, lol.

---

### Post by lynx93 on 2009-08-07
Thank you very much guys, Cairo works really!

---

### Post by ubudog on 2009-08-07
> **mudcat said:**
> the stock themes change only color; if it's a theme that you downloaded from the web you need to install it. If you are looking for the "Mac" dock; i suggest you take a look at Awn window manager. If the mac theme is what your going for, check out Mac4Lin.

Yeah you would probably like mac4lin.  :)

---

