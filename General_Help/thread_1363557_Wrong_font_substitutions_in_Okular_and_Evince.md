---
title: "Wrong font substitutions in Okular and Evince"
date: 2009-12-24
forum: General Help
---

### Post by philpem on 2009-12-24
Ubuntu ver: 9.10, x86_64

Hi
I noticed the fonts were "bunched up" in a PDF I was viewing, so I checked the fonts tab in Okular's file-info window. This revealed that Okular was substituting DejaVu-Sans for NewCenturySchlbk-Roman -- i.e. swapping a sans-serif font in for a serif font (a better substitution would be e.g. DejaVu Serif).

I've installed the TTF version of NewCenturySchlbk ("New Century Schoolbook") in my ~/.fonts directory, and re-run mkfontdir and fc-cache over it. Even after this, Okular is doing the same thing -- bunched up fonts, wrong substitution.

Can someone please tell me what I'm doing wrong here? Even fontconfig seems to be confused -- 
```

$ fc-match "NewCenturySchlbk-Roman"
DejaVuSans.ttf: "DejaVu Sans" "Book"

```

Thanks,
Phil.

---

### Post by lorenzosu on 2010-01-11
I have the same problem with a PDF file which reports to use MTimesNewRoman which is substituted in both evince and Okular with Dejavu Sans.. In fact it should use a serif (or as I have it on the system use Times New Roman)
XPdf displays the file correctly.
Ubuntu versin is 9.10.

Lorenzo

---

### Post by lineinthesand on 2012-03-23
I'm on openSUSE and I had the same problem; I solved it like this:

I added this to my ~/.fonts.conf (just before the closing </fontconfig> tag):
```

 <match target="pattern">
   <test qual="any" name="family"><string>NewCenturySchlbk</string></test>
   <edit name="family" mode="assign" binding="same"><string>Century Schoolbook L</string></edit>
 </match>

```
Then I did 
fc-cache
and now 
fc-match NewCenturySchlbk
gives: 
c059013l.pfb: "Century Schoolbook L" "Roman"

Evince and Okular both display a proper font (don't know the difference between NewCenturySchlbk and Century Schoolbook L, but it looks quite good).

On openSUSE, Century Schoolbook L is contained in the package ghostscript-fonts-std, by the way.

---

### Post by sasasasasasa on 2013-03-13
I can confirm the same problem in okular 0.15.5 in kubuntu 12.10 and it is quite bad (document unreadable in okular rendered perfectly in acroread).

The fix given by lineinthesand above works perfectly (only I just added the line and restarted okular, the fc-cache stuff I didn't need).

---

### Post by sasasasasasa on 2013-03-14
Ok - qualifier to the previous post - with this fix (in .config/fontconfig/fonts.conf okular renders the document perfectly on screen but doesn't print or produce a print preview - it will print a document that doesn't contain the offending fonts.  It produces no errors that I can find.

However this appears to be this bug: [https://bugs.kde.org/show_bug.cgi?id=293625](https://bugs.kde.org/show_bug.cgi?id=293625)

and the rerendering through gs (gs -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=out.pdf ex1.pdf) works ok on screen and in print for okular

I should add that the file in question renders perfectly onscreen for acroread but has incorrect kerning in print for acroread.

---

### Post by codemaniac on 2013-03-14
Closed old thread.

As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old. Feel free to start a fresh thread.

Thanks!

---

