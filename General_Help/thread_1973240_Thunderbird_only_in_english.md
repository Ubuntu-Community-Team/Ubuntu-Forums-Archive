---
title: "Thunderbird only in english?"
date: 2012-05-04
forum: General Help
---

### Post by HannuMR on 2012-05-04
Ubuntu 10.04
My language is finnish, and today by update Thunderbird 12.0.1 is in english, and I can not change language even there is thunderbird-locale-fi package, and I remove thunderbird-locale-en, thunderbird-locale-en-gb, thunderbird-locale-en-us - it is still in english.
How to change language?

:confused:

---

### Post by guestolo on 2012-05-04
See if you can get help from the following link

[http://kb.mozillazine.org/Change_Default_Mozilla_Language#Downloading_a_language_pack](http://kb.mozillazine.org/Change_Default_Mozilla_Language#Downloading_a_language_pack)

---

### Post by HannuMR on 2012-05-04
> **guestolo said:**
> See if you can get help from the following link

[http://kb.mozillazine.org/Change_Default_Mozilla_Language#Downloading_a_language_pack](http://kb.mozillazine.org/Change_Default_Mozilla_Language#Downloading_a_language_pack)

Thanks a lot guestolo!!

I make it this way, and now language is what I want:

"Note:  To install a language pack in Thunderbird, do not click the link to the xpi file. Instead, open Thunderbird's Extensions or Add-ons window, then drag the link from your browser and drop it there."

):P

---

### Post by Ubunky on 2012-05-05
I've got the same problem. Ubuntu 10.04. Thunderbird is in english even if thunderbird-locale-de is installed.

I've tried the same thing as HannuMR and dragged "de.xpi" from [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/12.0.1/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/12.0.1/linux-i686/xpi/) into the addon screen of Thunderbird 12.0.1.

A dialog pops up and asks if I want to install the german language pack. This is where it stops. I click the "Install now" button at the bottom right but nothing seems to happen. I wait for about 30 seconds and press it again. Then the dialog disappears. Nothing else. Any tips?

---

### Post by Hannu Mikael on 2012-05-05
I am still HannuMR.

Question for folk in Canonical.
Why I can not get package "thunderbird-globalmenu?"
It is in newer Ubuntus, and there is not this language problem.
Is this the main reason in Ubuntu 10.04?

---

### Post by Hannu Mikael on 2012-05-07
[Ubunky]("http://ubuntuforums.org/member.php?u=581825")

New way (funny)
- Save file de.xpi 
- Send it to your self via Thunderbird 
- Click file
- Installation starts
- Close and open Thunderbird

[http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/latest/win32/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/latest/win32/xpi/)

---

### Post by Ubunky on 2012-05-10
Hi Hannu Mikael,

I've tried it, but it doesn't work. There's no difference between sending the .xpi file to yourself and clicking it compared to opening **Tools - Add-ons** and choosing *Install Add-on from file...* from the 'Tool for all add-ons'- drop down menu on the left side of the search bar in the upper right corner.

In both cases the Install dialog pops up and when I click "Install Now" nothing happens.

Are you sure about using the win32 xpi file? I'm using TB on Ubuntu so I thought [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/12.0.1/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/12.0.1/linux-i686/xpi/) would be the right de.xpi.

Meanwhile my TB interface reads still english and I've got no clue how to change that. :( But thanks for your help anyway. :)

---

### Post by Hannu Mikael on 2012-05-11
Ubunky

In my case those both sources dont have difference.
[http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/latest/win32/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/latest/win32/xpi/)
[http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/12.0.1/linux-i686/xpi/](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/12.0.1/linux-i686/xpi/)
Have you tried to send de.xpi to yourself via Gmail?
Somebody did it in that way.

---

### Post by Ubunky on 2012-05-17
.../win32/xpi -> 28-Apr-2012 17:49  446K
.../.-i686/xpi -> 28-Apr-2012 17:05  409K

looks different to me. As for the "sending it to yourself" this doesn't make any changes to the .xpi. So why not installing it with *Install Add-on from file...*?

Like I said, I tried it nevertheless and it didn't work. After clicking on "Install Now" nothing happens.

---

### Post by tormod on 2012-12-25
I have filed a bug report and a workaround here: [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1093678](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1093678)

```

sudo apt-get remove thunderbird
sudo apt-get install thunderbird-locale-nb

```

Of course, on Ubuntu you are not supposed to have to install the xpi files in the GUI if you have the correct language pack installed. The problem is that after upgrading from previous versions of Thunderbird, /usr/lib/thunderbird/extensions/ is a directory instead of a soft link to ../thunderbird-addons/extensions

---

