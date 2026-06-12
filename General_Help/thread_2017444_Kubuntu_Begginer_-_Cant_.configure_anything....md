---
title: "Kubuntu Begginer - Cant ./configure anything..."
date: 2012-07-05
forum: General Help
---

### Post by KYSkud on 2012-07-05
Hey all so I'm really new to Kubuntu and have been trying to learn as much as I can about the process of installing programs but Im afraid I've hit a snag.

So this all started because I'm trying to install a Qtcurve theme on my new kubuntu. To get the Qt to show up in the system settings -> widget style list I had to have the QtCurve Gtk2, KDE3 and KDE4 packages. So I downloaded those source files, but when I tried installing them I realized I couldnt even run the ./configure command. I saw that I needed pkg-config-0.26 for ./configure to work properly, but I cant use the ./configure command to even install pkg-config so how do I get past this?

This is probably a really stupid question and I feel like I'm lacking knowledge on an integral process of how installing even works in kubuntu but thanks for any help!

---

### Post by oldos2er on 2012-07-05
Can you provide a link to the theme you want to install?

---

### Post by KYSkud on 2012-07-05
[http://kde-look.org/content/show.php/?content=97644](http://kde-look.org/content/show.php/?content=97644)

But there appears to be a deeper problem, in that I cant ./configure any source folder

---

### Post by robtygart on 2012-07-05
**From the Read Me file.....**

This is a theme for KDE4 and QtCurve.

QtCurve 1.0.1 or later recommended. This version of darkPearl may not work
correctly with earlier versions of QtCurve.

Installation instruction:

1) Import the KDE4 color scheme found in the package (darkPearl.colors)
   in System Settings --> Appearance --> Colors --> Import Scheme.

2) Select QtCurve as the Widget style in System Settings --> Appearance -->
   Style. Click on "Configure" then on "Import" inside the QtCurve settings
   window and select darkpearl.qtcurve.

3) Go to System Settings --> Apperance --> Windows and select QtCurve as the
   decoration. It is recommended that the border size is set to tiny and the
   "Draw dark outer border" checked.


**Note:** Using KDE there are some import buttons after installing themes. Its always good to extract the files you downloaded and look for a Read Me file.

---

### Post by KYSkud on 2012-07-05
Yeah I read that already. I completed step 1 fine but ran into trouble with step 2.  It did not show the QTCurve option listed in System Settings --> Appearance --> Style. Fixing that problem requires me to install a package, which is why I posted originally that the root problem was me not being able to run ./configure in source folders

---

### Post by SeijiSensei on 2012-07-05
Usually running ./configure means you have to compile something from source.  You're probably just missing the compilation environment which isn't installed by default.  Try running

```
sudo apt-get build-dep
```

and then try ./configure again.

---

### Post by robtygart on 2012-07-05
> **KYSkud said:**
> Yeah I read that already. I completed step 1 fine but ran into trouble with step 2.  It did not show the QTCurve option listed in System Settings --> Appearance --> Style. Fixing that problem requires me to install a package, which is why I posted originally that the root problem was me not being able to run ./configure in source folders

It just changed my colors 

Here is what I did.

> Extract the file.

Go to: System Settings --> Appearance --> Colors --> Import Scheme.

Open the extracted folder and slect the file called darkPearl.colors 

Apply

Did that change anything? 

I still can't figure out what he is talking about in step 2... :?:

---

### Post by KYSkud on 2012-07-05
> **SeijiSensei said:**
> Usually running ./configure means you have to compile something from source.  You're probably just missing the compilation environment which isn't installed by default.  Try running

```
sudo apt-get build-dep
```and then try ./configure again.
I get this message when I try that in konsole "E: Must specify at least one package to check builddeps for"

And yeah robtygart we have the same issue. Step 1 worked perfectly, I imported the colors and applied the new settings, but I couldnt complete step 2....

---

### Post by SeijiSensei on 2012-07-06
> **KYSkud said:**
> I get this message when I try that in konsole "E: Must specify at least one package to check builddeps for"

I'm sorry!  That's the wrong "build-" parameter.  Try this:

```
sudo apt-get build-essential
```

The build-dep command is also very useful.  If you give it the name of an application, it will install all the libraries and "header" files you would need to compile the application from scratch.  For instance,

```
sudo apt-get build-dep mplayer
```

would download everything you need to build a copy of mplayer from its source code.

---

### Post by BigCityCat on 2012-07-06
When you go into system settings the menu that says style and then oxygen is a drop down menu. If you press it it will give you more options. QTcurve is at the bottom. Then after you set qtcurve and then hit the button to the right you can import the theme you are trying to use.

To install qtcurve open a terminal and sudo apt-get install qtcurve

It's in the repositories. If you have sysnaptic installed you can search for it. Keep trying to learn. In the end you will be happy you did. The good thing is you can keep re installing till you learn what you are doing. It wasn't long ago and I was in the same boat.

---

### Post by robtygart on 2012-07-06
> **BigCityCat said:**
> When you go into system settings the menu that says style and then oxygen is a drop down menu. If you press it it will give you more options. QTcurve is at the bottom. Then after you set qtcurve and then hit the button to the right you can import the theme you are trying to use.

To install qtcurve open a terminal and sudo apt-get install qtcurve

It's in the repositories. If you have sysnaptic installed you can search for it. Keep trying to learn. In the end you will be happy you did. The good thing is you can keep re installing till you learn what you are doing. It wasn't long ago and I was in the same boat.

Cool that worked! Thank you...

---

### Post by BigCityCat on 2012-07-07
No problem now mark this thread as solved with thread tools.

---

### Post by robtygart on 2012-07-08
> **BigCityCat said:**
> No problem now mark this thread as solved with thread tools.

I am not the OP, but I was trying to get it working on mine too.

---

