---
title: "VLC crashes when opening a movie"
date: 2010-02-07
forum: General Help
---

### Post by DeMus on 2010-02-07
When starting VLC I get the following message:

VLC media player 1.0.2 Goldeneye
[0xa18888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x11062b8] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 133.19 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  133 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  101
  Current serial number in output stream:  102

Anyone an idea what this might be?

Never mind. Found it. Just for the fun of it I installed Cairo-dock and it was messing with VLC. After a re-boot I did not start Cairo and now the movie plays fine.
So, I un-installed Cairo.

---

### Post by fabounet on 2010-02-07
the real solution is just to install the latest version of VLC which fixes the bug, or to disable the option "Integrate video in interface"

---

### Post by DeMus on 2010-02-07
> **fabounet said:**
> the real solution is just to install the latest version of VLC which fixes the bug, or to disable the option "Integrate video in interface"

Thank you for your help. I looked around and for Jaunty the latest one I could find is the 1.02 version which I have. Can you find a newer one?
In 1.02 where can I find the option you mentioned? I searched through all the options and I don't find it.

---

### Post by bilalsultan86 on 2010-03-15
Hey,

I tried all type of solutions available on different solutions including ubuntuforum.org but they all failed. 
Then a very simple solution worked for me..Its
**SOLUTION**
Option 1: Go to Tools -> Preferences and uncheck embed video in interface.
Option 2: Switch to OpenGL video output mule in the preference. Tools -> Preference -> Video; In Output select OpenGL video output -> Save 
 and done!!
 Ref [[1]("http://ubuntuforums.org/archive/index.php/t-1232781.html")]
-Abhi

Details of solution are available at [http://akdwivedi.wordpress.com/2009/12/27/solution-vlc-crashes-in-ubuntu-9-10/#comment-48](http://akdwivedi.wordpress.com/2009/12/27/solution-vlc-crashes-in-ubuntu-9-10/#comment-48)

Thankyou Abhi.:popcorn:

---

