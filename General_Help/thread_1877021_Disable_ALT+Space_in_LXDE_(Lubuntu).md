---
title: "Disable ALT+Space in LXDE (Lubuntu)"
date: 2011-11-07
forum: General Help
---

### Post by codefenix on 2011-11-07
I decided to try out LXDE on my Xubuntu 11.04 build.  Problem though...  The ALT+Space keyboard combination *always*  brings up the window menu for the active application, no matter what  the application is.  Press ALT+Space now for an example of what I'm talking about.   As anyone who uses MAME can imagine, this is especially annoying.

I  already deleted all keyboard shortcuts under Xubuntu.  When I toggle back  and forth between window managers, XFCE behaves as desired but LXDE always insists on bringing up this menu.

I've done some  Googling, and discovered that LXDE doesn't have a keyboard shortcut  GUI-- it's all done by editing an XML file.  When I look at this file,  there's nothing that defines this specific shortcut. It's almost like  it's hard-coded into the UI.

So how can I turn this keyboard shortcut off?  Is it possible?  Does the same thing happen under pure Lubuntu?

---

### Post by croque on 2011-11-07
The following disables the Alt-Space function on my fresh install of Lubuntu 11.10 (can't say if it would work on LXDE 11.04):

1. Open ~/.config/openbox/lubuntu-rc.xml
```
leafpad ~/.config/openbox/lubuntu-rc.xml
```2. Find and remove this section of text:
```
<keybind key="A-space"><action name="ShowMenu"><menu>client-menu</menu></action></keybind>
```3. Save the file.

4. Log out and log back in.

That should do it.

---

### Post by codefenix on 2011-11-07
Hmm.. Could have sworn I didn't see anything like that in the file.  I'll give it another look this afternoon when I get home!

Here's hoping!  Thanks, Croque!

---

### Post by croque on 2011-11-07
I also have the files lxde-rc.xml and rc.xml in that directory (~/.config/openbox/). If you're running straight LXDE rather than Lubuntu, one of those files might be controlling your keybindings.

---

### Post by amjjawad on 2011-11-07
> **codefenix said:**
> I decided to try out LXDE on my Xubuntu 11.04 build.  Problem though...  The ALT+Space keyboard combination *always*  brings up the window menu for the active application, no matter what  the application is.  Press ALT+Space now for an example of what I'm talking about.   As anyone who uses MAME can imagine, this is especially annoying.

I  already deleted all keyboard shortcuts under Xubuntu.  When I toggle back  and forth between window managers, XFCE behaves as desired but LXDE always insists on bringing up this menu.

My Personal Opinion: I don't recommend such build for daily use. One could try many other ways which IMHO are much better than this way (installing LXDE or Lubuntu Package rather than install the OS itself). One of these ways: Live-USB, Installing Lubuntu on USB Drive, Virtual Machine and of course normal installation.

I'm NOT saying what you have done was wrong, but it will bring more headache. Again, this is my personal opinion.

> I've done some  Googling, and discovered that LXDE doesn't have a keyboard shortcut  GUI-- it's all done by editing an XML file.  When I look at this file,  there's nothing that defines this specific shortcut. It's almost like  it's hard-coded into the UI.
There is no GUI application yet for that (as far as I know).
Have a look at: [http://wiki.lxde.org/en/LXDE:Questions#Keyboard.2FMouse](http://wiki.lxde.org/en/LXDE:Questions#Keyboard.2FMouse)

>   Does the same thing happen under pure Lubuntu?
It should be fairly easy on Lubuntu.

---

### Post by codefenix on 2011-11-07
I found it.  In my file, all of my keybindings for desktop switching, windows, and window switching were all inline with one another.  When I didn't know what I was looking for, it never "popped" into view because I never bothered to scroll horizontally (silly me).  So it was helpful to know exactly what keybind text to search for, and "A-Space" was it as you pointed out.  I deleted all of these keybindings (I don't need them in my cabinet), and all is well.  Thanks so much for the help!

> I don't recommend such build for daily use. One could try many  other ways which IMHO are much better than this way

I know.  As I said, this is my crude way of test driving LXDE without  doing a full-blown Lubuntu install.  Thanks for the advice, all the  same.

---

### Post by croque on 2011-11-07
It's the same way in my lubuntu-rc.xml file...all the keybindings in one long line. Not sure why.

---

### Post by amjjawad on 2011-11-07
> **croque said:**
> It's the same way in my lubuntu-rc.xml file...all the keybindings in one long line. Not sure why.

One place is better ;)

---

### Post by croque on 2011-11-07
To make the file more readable, you can use xmlindent:

```
xmlindent ~/.config/openbox/lubuntu-rc.xml | less
```

Doesn't change the file...just outputs it nicely formatted.

---

### Post by amjjawad on 2011-11-08
> **croque said:**
> To make the file more readable, you can use xmlindent:

```
xmlindent ~/.config/openbox/lubuntu-rc.xml | less
```Doesn't change the file...just outputs it nicely formatted.

It's not installed by default so:

```
sudo apt-get install xmlindent
```

However, this is just to view, you can't edit.

---

### Post by techvish81 on 2011-11-08
hello everyone, my question is to amjawad,
i tried lubuntu, xubuntu,ubuntu everything in my netbook, the most snappier i found was lubuntu, my main pc (desktop) is quite stable with ubuntu and i have no plans to change anything in it,it is my work computer and i cant experience anything, so i use my netbook to experience various distros, lubuntu is by far the best i would suggest to anybody but there is only one problem for which ,still i have not found any solution,  i want to use libreoffice and chromium and nothing else in it, my problem is that even if i put a keyboard layout switcher in the panel i was unable to install more languages, i installed ibus tried everything in the threads but nothing happens, the option in the input method menu remains greyed and it doesnt allow me to add more languages to my system language which is english (us).
in xubuntu, just a plugin install can do it, in ubuntu it works out of the box. 

any straight forward way would be highly appreciated, 

in context to the above posts , i would recommend lubuntu rather than installing lxde on ubuntu, ; lubuntu is much fine tuned and user friendly than pure lxde.
 
cheers!!

---

### Post by codefenix on 2011-11-08
> **amjjawad said:**
> One place is better ;)

I hope you're kidding!  The difference between XML code being all on one line and on separate lines is negligible as far as the XML parser is concerned.  I would think it's always better to space it out for human readability's sake.

[QUOTE=techvish81]in context to the above posts , i would recommend lubuntu rather than  installing lxde on ubuntu, ; lubuntu is much fine tuned and user  friendly than pure lxde.[/QUOTE]

Again, I was just kicking the tires on the LXDE window manager before committing to doing a clean Lubuntu install.  I appreciate the opinion though.

---

### Post by amjjawad on 2011-11-08
> **codefenix said:**
> **I hope you're kidding**!  The difference between XML code being **all on one line** and on separate lines is negligible as far as the XML parser is concerned.  I would think it's always better to space it out for human readability's sake.
Perhaps I wasn't clear enough :)
I meant, the whole thing on **ONE FILE** not ***ONE LINE*** ;)

---

### Post by amjjawad on 2011-11-08
> **techvish81 said:**
> hello everyone, my question is to amjawad,
i tried lubuntu, xubuntu,ubuntu everything in my netbook, the most snappier i found was lubuntu, my main pc (desktop) is quite stable with ubuntu and i have no plans to change anything in it,it is my work computer and i cant experience anything, so i use my netbook to experience various distros, lubuntu is by far the best i would suggest to anybody but there is only one problem for which ,still i have not found any solution,  i want to use libreoffice and chromium and nothing else in it, my problem is that even if i put a keyboard layout switcher in the panel i was unable to install more languages, i installed ibus tried everything in the threads but nothing happens, the option in the input method menu remains greyed and it doesnt allow me to add more languages to my system language which is english (us).
in xubuntu, just a plugin install can do it, in ubuntu it works out of the box. 

any straight forward way would be highly appreciated, 


Hi,

I'd appreciate if you start a new thread and then send me the link of your new thread :)

Thanks!

---

### Post by codefenix on 2011-11-08
> **amjjawad said:**
> Perhaps I wasn't clear enough :)
I meant, the whole thing on **ONE FILE** not ***ONE LINE*** ;)

But everything being on one line is exactly what you commented on... 
:confused:

[QUOTE=codefenix]In my file, all of my keybindings for desktop switching, windows, and window switching were **all inline with one another**[/QUOTE]
[QUOTE=croque]It's the same way in my lubuntu-rc.xml file...**all the keybindings in one long line. **Not sure why.[/QUOTE]
[QUOTE=amjjawad]One place is better [/QUOTE]

---

### Post by amjjawad on 2011-11-08
> **codefenix said:**
> But everything being on one line is exactly what you commented on... 
:confused:

Again, my apology if I was not clear enough but yet again, I'm confirming that I was talking about having all that code in one file NOT one line. Never mind, no big deal :)

Having 10 tabs opened, each with different thread is fair enough to make me lose focus and not clear enough. Keep telling myself to slow down but ... can't resist :)

---

