---
title: "Ubuntu changed the font of the website"
date: 2011-05-16
forum: General Help
---

### Post by Jerriy on 2011-05-16
I bumped into this site that's supposed to look like this:[INDENT][IMG]https://lh5.googleusercontent.com/_-BKdOEuV088/TdFcJEDznUI/AAAAAAAADKo/aKnmKG0Hju0/normal.png[/IMG][/INDENT]But on my ubuntu firefox browser it looks like this:[INDENT][IMG]https://lh3.googleusercontent.com/_-BKdOEuV088/TdFe5cywSrI/AAAAAAAADK8/S0_vlKQC1FA/wrong.png[/IMG][/INDENT]What on earth did that? 
And needless to say what's the fix?

---

### Post by Jerriy on 2011-05-16
The problem didn't go away

---

### Post by mikewhatever on 2011-05-16
Do you use NoScript? If so, allowing aolcnd.com makes the fonts scale properly.
PS: Providing a link would have been useful.
[http://www.huffingtonpost.com/](http://www.huffingtonpost.com/)

---

### Post by Jerriy on 2011-05-16
> **mikewhatever said:**
> Do you use NoScript? If so, allowing aolcnd.com makes the fonts scale properly.
PS: Providing a link would have been useful.
[http://www.huffingtonpost.com/](http://www.huffingtonpost.com/)You mean aolc**dn**.com? 

Doesn't make a difference. I still have the same problem.

---

### Post by grahammechanical on 2011-05-16
In Firefox go to View and select Character encoding and make sure that it is using Unicode (UTF-8 ) because that is the charset that the page is set to. Open the page and right click on it and select View Page Source. Another thing, Firefox may be using a default font to render some parts of the page because the font chosen by the page designer is not on your system.

Regards.

---

### Post by mikewhatever on 2011-05-16
Try allowing huffpost.com and aolcdn.com.

---

### Post by lavinog on 2011-05-16
It could be that you do not have the font that they are using:
```

.top_nav_menu ul li a {
font-family: 'HelveticaNeueLT57CnBold';
font-size: 15px;
font-weight: normal;
}

```

You should try installing the ttf-mscorefonts-installer
[Click here to install](apt://ttf-mscorefonts-installer)

---

### Post by Jerriy on 2011-05-17
> **grahammechanical said:**
> In Firefox go to View and select Character encoding and make sure that it is using Unicode (UTF-8 ) because that is the charset that the page is set to. Open the page and right click on it and select View Page Source. 

Regards.Done that, it's utf 8, I even customized the encoding and removed the other code (western) from the "active list" and allowed only utf 8 to be active, but still no change.

> Another thing, **Firefox may be using a default font to render some parts  of the page** because the font chosen by the page designer is not on your  system.And how do I find out whether that's the case or not?

> Try allowing huffpost.com and aolcdn.com.Dun all that even completely disabled the extension but to no avail.

---

### Post by Jerriy on 2011-05-17
> **lavinog said:**
> It could be that you do not have the font that they are using:
```

.top_nav_menu ul li a {
font-family: 'HelveticaNeueLT57CnBold';
font-size: 15px;
font-weight: normal;
}

```You should try installing the ttf-mscorefonts-installer
[Click here to install]("apt://ttf-mscorefonts-installer")Did that and got the message that mscorefonts is already installed. And via synaptic I can see that it is indeed installed (I ticked "reinstall" anyway but that didn't solve anything either)

What exactly is the command to get a list of fonts installed AND functioning properly (I suspect that despite the mscorefonts being installed there is no Helvetica in my list of fonts as far as I can see (via office applications).

---

### Post by Jerriy on 2011-05-17
Why is there no EXCLUSIVE font management (not only viewing but installing and removing individual fonts) program in Ubuntu? 

Windows had it way back in the 3.1 days!

---

### Post by mikewhatever on 2011-05-17
> **Jerriy said:**
> ...

Dun all that even completely disabled the extension but to no avail.

Really interesting. Allowing those two fixes the scaling here, which was originally the same as in your screenshot. What if you try running firefox in safe mode (extensions and themes disabled)?
```
firefox -safe-mod
```

---

### Post by Jerriy on 2011-05-17
Dun that. Still no difference. 

The brower configuration is somehow screwed. Cuz a different account login (after same single boot-up of the machine) didn't cause this problem so it can't be a font issue me thinks.

Something in about:config or whatever must be crooked

---

### Post by Jerriy on 2011-05-17
I just noticed that when my browser opens, the character encoding automatically switches to "Western ISO 8859-1" even after I deliberately ticked Unicode UTF 8

What on earth is going on? Help!

---

### Post by Jerriy on 2011-05-17
Solved!

---

### Post by lavinog on 2011-05-19
> **Jerriy said:**
> Solved!

How was it solved?

---

### Post by Jerriy on 2011-05-20
> **lavinog said:**
> How was it solved?Actually it came back. 

I had another profile and so I deleted the problematic profile that I was using and switched to this other reserve one (thinking that the problem had gone)

But alas! The same thing suddenly showed up again in the new profille :twisted:
.

---

### Post by Jerriy on 2011-05-20
[IMG]https://lh3.googleusercontent.com/_-BKdOEuV088/TdclkjStokI/AAAAAAAADQE/KiPrEc5EeLs/screenshot.png[/IMG]

---

### Post by Jerriy on 2011-05-21
Help!

Now here's another site 'deadspin.com' that is showing NOTHING on the ubuntu machine in front of me:

[IMG]https://lh6.googleusercontent.com/_-BKdOEuV088/Tdc9NLzeDXI/AAAAAAAADQI/ExqLRpNspvU/screenshot.png[/IMG]


I tried by enabling and disabling ALL extensions but that made no difference.

Can someone help me WTF is going on?

---

### Post by linuxinstalledfromhdd on 2011-05-21
can you reset your zoom on your browser?

---

### Post by Jerriy on 2011-05-21
Yes I can zoom in and out and reset (ctrl+0), that part seems to be working as normal

---

### Post by linuxinstalledfromhdd on 2011-05-21
I just tried to replicate what you are trying to do. I was successful. 

In firefox I selected 'View'.. Then selected Character Encoding..  Closed out of the browser.  The rechecked and setting was saved.  

Whatever you are experiencing is strange indeed.

---

### Post by Jerriy on 2011-05-21
What is "page style" and what's the normal/default setting for it? It's found in the ff menu "View" right above "Character encoding"

I'm asking cuz I noticed that the available options there seem to change automatically: I have 2 tabs open and in one tab (the one this forum is opened on) the sub-menu options are "no style" and "basic page style" whereas in another tab with another webpage the available options are "no style", "A", "A+" and "A++" in that order.
[COLOR=White].[/COLOR]

---

### Post by snerd on 2011-05-21
> **mikewhatever said:**
> Try allowing huffpost.com and aolcdn.com.

Friends don't let friends read huffpo.  :P

---

