---
title: "Windows fonts"
date: 2010-08-28
forum: General Help
---

### Post by Poga on 2010-08-28
I have a problem regarding Windows fonts that I can't seem to find for Ubuntu.

I've installed "Ubuntu restricted extras" already, but still have a significant problem concerning fonts that I need to use for my job.  I'm currently using Lucid (10.04.1).  There are three fonts I commonly use on Windows machines, but I haven't found a way to get them on Ubuntu.  They are: "Century Gothic", "Copperplate Gothic Light", and "SimSun" (a Chinese font).

Does anyone know if it's possible for me to get these fonts on Ubuntu somehow?

---

### Post by Ginsu543 on 2010-08-28
There are two places you can copy truetype fonts to to get them to work in Ubuntu. First is /usr/share/fonts/truetype and the second is /home/<user_name>/.fonts. When you install ubuntu-restricted-extras, it installs msttcorefonts to /usr/share/fonts/truetype. I suggest you try copying the fonts you want to the .fonts folder inside your /home/<user_name> folder. Notice the "." in front, which means that it is a hidden file. You will need to hit Ctrl+H in Nautilus to see it. If it's not there, just create a new folder and name it .fonts.

---

### Post by hawthornso23 on 2010-08-28
Installing fonts is totally easy. Just put the .ttf file anywhere. Double click to open it with font viewer and click the button to install. It'll put it in the right place automagically and you'll be able to use it in openoffice etc.

---

### Post by Poga on 2010-08-28
Thanks.  I appreciate both of the responses I received.  Once I find the font files, your instructions will be very helpful.  I'm still a little confused regarding the process of obtaining the fonts themselves, however.

Is there some repository where I can find the fonts?  (They were all included by default in my previous Windows XP installation.)  Or will I need to swipe Ubuntu and re-install Windows (a rather time-consuming process), and then find/copy the files manually from the XP folders?  (If I did this, would the files have any sort of DRM or copy-protection that would prevent me from using them on Ubuntu?)

I also don't know if I need just one font file, or multiple files for one font.  For example, would Gothic.ttf (for "Century Gothic") be enough, or would I also need ttf's for bold, italics, and bold/italic?

I spent a couple of hours Googling all of this, but found many inconsistent and seemingly untrustworthy files, from rather sketchy places.  Any suggestions?

---

### Post by hawthornso23 on 2010-08-28
> **Poga said:**
> Thanks.  I appreciate both of the responses I received.  Once I find the font files, your instructions will be very helpful.  I'm still a little confused regarding the process of obtaining the fonts themselves, however.

Is there some repository where I can find the fonts?  (They were all included by default in my previous Windows XP installation.)  Or will I need to swipe Ubuntu and re-install Windows (a rather time-consuming process), and then find/copy the files manually from the XP folders?  (If I did this, would the files have any sort of DRM or copy-protection that would prevent me from using them on Ubuntu?)

I also don't know if I need just one font file, or multiple files for one font.  For example, would Gothic.ttf (for "Century Gothic") be enough, or would I also need ttf's for bold, italics, and bold/italic?

I spent a couple of hours Googling all of this, but found many inconsistent and seemingly untrustworthy files, from rather sketchy places.  Any suggestions?

Suggestion:  Take a USB key. Plug it into any windows machine (it doesn't have to be the latest greatest - those fonts are ancient - XP is fine). Copy the windows fonts directory  ( probably C:\\windows\fonts or similar ) onto the USB key. All the TTF files are in there. They are not encrypted or anything. Plug the USB key into your linux box. Browse and install what you want. 

OK - There may be licensing implications. The exact legal situation varies depending on jurisdiction and who owns the windows machine you copy the files across from etc etc. The reason people are not being explicit on the internet is probably because of this potential copyright issue.

Morally speaking I see no issue however. Microsoft through their monopolistic licensing practices forces us to buy their unwanted crap in order to get the hardware we want. When we delete windows to install ubuntu the least we can do is scavange a few useful parts. If you've ever bought hardware with windows on it you've paid for those font files. You might as well get some use out of them.

---

### Post by kelvinho on 2010-08-28
Hi Poga. Copy the fonts over from your Windows Partition, or get them from a friend.

Alternatively, a simple search can reveal a lot. Try "win 7 fonts.deb" in your Google search box.

If you consider these dubious sources, you can try here;

[http://office.microsoft.com/en-us/marketplace/CE001073747.aspx](http://office.microsoft.com/en-us/marketplace/CE001073747.aspx)

The whole point about Linux is that there always exists an alternative. Try searching in the package directory with Synaptic.

Hope I have been of some help.

---

### Post by Ginsu543 on 2010-08-28
Your best bet is to copy over the fonts from Windows. You can also download some of the fonts for free. For example, you can get CopperPlate Gothic from [_this_](http://www.webpagepublicity.com/free-fonts-c4.html#Free%20Fonts) website.

Whether you need to install one or multiple truetype files for each typeface depends on the truetype file. Some contain all the data you need for the normal, bold, and italic versions. In most cases, however, you will need to install separate .ttf files for each style.

---

### Post by Poga on 2010-08-30
Thanks everyone.  You've all been a big help.  As frustrating as having a computer problem can be sometimes, I've often found it to be one of the best ways to learn.  (I'm still thankful for my first real computer crash, years ago.)

Anyway, thanks for the info regarding the fonts.  It made things a lot easier for me.

---

