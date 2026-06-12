---
title: "Font Antialiasing: XP vs. Ubuntu (Spoiler: XP Wins)"
date: 2009-12-25
forum: General Help
---

### Post by sgiandubh on 2009-12-25
Calibri is a great typeface, having been designed for the screen by Lucas de Groot of LucasFonts. As you probably know by now, Calibri became the default typeface for the Microsoft Office family of products starting with the 2007 edition. Ubuntu, and Linux in general, is an excellent OS with which I feel more productive; unfortunately, the font antialiasing configuration (or implementation) is atrocious.

Initially, I thought the problem was limited to OpenOffice, but this turned out to not be the case. I thought installing Office 2007 would address my complaint, but someone showed me a screenshot of Office 2007 installed in Ubuntu, and no, font antialiasing had not improved. I tried the various solutions found on these forums and in search results, from editing .fonts.conf to tweaking xorg.conf to linking different conf.d configurations to using the Gnome Appearance manager. None of the solutions have worked for me, so consider this a cry for help.

The following are screenshots of Calibri at sizes 6 through 32 as displayed in Word 2007 on Windows XP and Writer on Ubuntu 9.10.

You should notice that font antialiasing in Ubuntu seems to be erratic. Calibri appears antialiased from sizes 6 to 9, 10.5, and then 15 and up. At sizes 10 and 11 to 14, Calibri is 1-pixel thin. You should also notice that the letterspacing of Calibri is unattractive in both applications but moreso in Writer. As an obvious example, contrast the space between "Cal" and "ibri" in 11 with the space between "Cali" and "bri" in 12. While these issues might seem trivial to the layperson, I was trained as a type designer and worked for many years as a graphic designer; these issues practically leap off the screen at me and bash my skull with a tire iron.

[CENTER]**Word 2007, Windows XP** (left) | **Writer, Ubuntu** (right)
[img]http://i49.tinypic.com/dc30pc.jpg[/img] [IMG]http://i50.tinypic.com/28rlg68.jpg[/IMG][/CENTER]

If there is no real solution, I guess I'll have to use Windows for word processing. I'm not keen on using relatively nonstandard alternative fonts or redesigning all of my documents, so these aren't solutions. I'm really hoping there's a *real* solution to my antialiasing woes. Anyone know the secret?

BTW: If I remember correctly, Calibri is weighted correctly in PDF versions of documents in Ubuntu.

---

### Post by sgiandubh on 2009-12-26
No solutions? :(

---

### Post by nortexoid on 2010-01-02
Here's a solution: Don't use Calibri! Ok, ok, it's not a very good solution. In fact, it may not be a solution at all if ANY font is antialiased better in XP. I hope that's not true, but this is an interesting find. Thanks for sharing.

By the way, have you checked the font antialiasing in XP in openoffice? Is it just Word that produces these results, or XP itself? If it's Word, that's another story...

---

### Post by dcstar on 2010-01-02
> **sgiandubh said:**
> 
........
BTW: If I remember correctly, Calibri is weighted correctly in PDF versions of documents in Ubuntu.

I just did this on my own OO Writer and the displayed fonts change appearance depending on the zoom you use.

Leave it at 100% and the Linux rendering does look like what you have displayed, but up it to 150% and the rendering looks totally different.

All you are seeing is an artefact of how OO Linux is displaying the font on the screen, if you actually use the document (like printing, conversion to PDF etc) it will probably render correctly.

---

### Post by Chandrashekhar on 2010-01-24
Hi,
To properly hint the calibri and like fonts in OpenOffice.org 3.1 do the following

Create a file in your home directory with the name .fonts.conf with following content:

Code:
    <match target="font" >
        <edit name="embeddedbitmap" mode="assign">
            <bool>false</bool>
        </edit>
    </match>

So now, finally, I have all my fonts under control.

---

### Post by isolationism on 2010-01-29
<match target="font" >
 <edit name="embeddedbitmap" mode="assign">
  <bool>false</bool>
 </edit>
</match>

... Works perfectly for me. Thank you very much, Chandrashekhar.

---

### Post by Heavenly Evil on 2010-11-11
Thank you so much! This has been driving me crazy.

---

