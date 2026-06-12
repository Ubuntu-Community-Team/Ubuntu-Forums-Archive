---
title: "xfig fonts problem: very strange"
date: 2006-04-10
forum: General Help
---

### Post by ashgarg on 2006-04-10
Hi All:

I am having a very strange problem with my xfig installation on Ubuntu Breezy (5.10). I installed the foillowing packages initially:
[I]
fig2ps
transfig
fig2sty
xfig
xfig-doc
xfig-libs
[/I]

When I started xfig after that from a terminal I get this:
[I]
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-medium-r-normal--16-*-*-*-*-*-*-*,*--16-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-medium-r-normal--16-*-*-*-*-*-*-*,-*-*-*-r-*--16-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Cannot convert string "-*-times-bold-r-normal--16-*-*-*-*-*-*-*,-*-*-bold-r-normal--16-*-*-*-*-*-*-*,-*-*-*-r-*--16-*-*-*-*-*-*-*" to type FontSet
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
[/I]

Now the xfig starts, but when I click on *T* for typing text and then click on the figure area, I get this error:
[I]
Can't find -*-times-medium-r-normal--13-*-*-*-*-*-ISO8859-*, using 6x13
[/I]

On a friends recommendation I installed the cyrillic font set as described here:
[I]
[http://dir.filewatcher.com/d/Ubuntu/all/tex/scalable-cyrfonts-tex_4.7_all.deb.10581772.html](http://dir.filewatcher.com/d/Ubuntu/all/tex/scalable-cyrfonts-tex_4.7_all.deb.10581772.html)
[/I]

I have no idea what is wrong but I am still gettting the same errors, even after restarting the xfs, restarting X server and even rebooting the machine.

I used to have hoary earlier and didn't have this problem with xfig. So I decided to go back and install hoary instead of breezy (lame I know), but now the hoary also has same problem.

Am I missing some sources which will include fixes to this?

I would really appreciate any help in this regard.

Thank you

---

### Post by ashgarg on 2006-04-14
I found the solution to my problem as described ([here]("https://launchpad.net/distros/ubuntu/+source/xfig/+bug/2066"))

   - "sudo dpkg-reconfigure locales" set default to ISO-8859-1 instead of UTF-8
   - put "xset fp rehash" in gnome-session. It must be run after each login.
   - run xfig with "LANG=C xfig"

hope this helps somebody

---

### Post by Predilications on 2006-05-22
Very useful. I solved my font problems by following your instructions (actually I added all of the en ISO-8859-1 choices to teh UTF-8 ones, rather than doing a replacement). Also I simply typed xfig at a command line to get xfig working. I did not need to run xfig with "LANG=C xfig", as far as I can make out.

THANKS!

---

### Post by hutxubix on 2006-06-15
Sorry,

I have the same problem, but I can't fix it because I don't know how to:
- set default to ISO-8859-1 instead of UTF-8 (I have not any choice with kpkg-reconfigure locales)
- put "xset fp rehash" in gnome-session.

Can somebody explain me how to do this things?

Thanks

---

### Post by bigM on 2006-09-14
I had this problem with xfig. I installed the following packages:

tkfont (1.1-12)
ttf-xfree86-nonfree (4.2.1-3)
unifont (1:1.0-1ubuntu2)

and now it works fine, apart from a few font selections. I haven't investigated which package was the necessary one. I assume it wasn't the first.

---

### Post by Pat Prodanovic on 2006-10-16
I have tried to "dpkg-reconfigure locales", but I can not see any ISO-8859-1 options. All that I see is this:

pat@panther:~$ sudo dpkg-reconfigure locales
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'America/Toronto'.
Local time is now:      Mon Oct 16 11:10:15 EDT 2006.
Universal Time is now:  Mon Oct 16 15:10:15 UTC 2006.
Run 'tzconfig' if you wish to change it.

Can someone help?

---

