---
title: "How To Change Font Size In Empathy"
date: 2010-10-26
forum: General Help
---

### Post by s0dium on 2010-10-26
Can anyone tell me how to change the font size in Empathy please? I would like to make it slightly smaller so I can fit more text in the chat window. Thanks for any help.

---

### Post by Script Warlock on 2010-11-03
a quick and simple workaround for added themes of empathy is by editing some lines inside the info.plist(backup that info.plist just incase).. 

adium matte theme: gksudo gedit and open the /usr/share/adium/message-styles/Adium Matte.AdiumMessageStyle/contents/info.plist  and find the line
<key>DefaultFontSize</key>
	<integer>12</integer>   <------ and change the font size to your likes then save.

---

### Post by markhu on 2010-12-09
mine was in a different path:

/usr/share/adium/message-styles/ubuntu.AdiumMessageStyle/Contents/Info.plist


> **Script Warlock said:**
> a quick and simple workaround for added themes of empathy is by editing some lines inside the info.plist(backup that info.plist just incase).. 

adium matte theme: gksudo gedit and open the /usr/share/adium/message-styles/Adium Matte.AdiumMessageStyle/contents/info.plist  and find the line
<key>DefaultFontSize</key>
	<integer>12</integer>   <------ and change the font size to your likes then save.

---

### Post by tumutanzi on 2011-03-12
Here is a webpage to show how to change the font type and font of Empathy in Ubuntu 10.04:
[http://www.tumutanzi.com/2011/03/change-font-size-and-type-of-empathy-in.html](http://www.tumutanzi.com/2011/03/change-font-size-and-type-of-empathy-in.html)

---

### Post by mirelon on 2011-04-05
> **tumutanzi said:**
> Here is a webpage to show how to change the font type and font of Empathy in Ubuntu 10.04:
[http://www.tumutanzi.com/2011/03/change-font-size-and-type-of-empathy-in.html](http://www.tumutanzi.com/2011/03/change-font-size-and-type-of-empathy-in.html)

The link is dead.

My Info.plist has no such key. I added those two lines and restarted Empathy, but no change.

(running Ubuntu 10.10)

---

### Post by akila87 on 2011-04-12
Try this link [http://tumutanzi.com/2011/02/change-font-size-and-type-of-empathy-in-ubuntu-10-04/](http://tumutanzi.com/2011/02/change-font-size-and-type-of-empathy-in-ubuntu-10-04/)

---

### Post by tumutanzi.com on 2011-09-29
> **akila87 said:**
> Try this link [http://tumutanzi.com/2011/02/change-font-size-and-type-of-empathy-in-ubuntu-10-04/](http://tumutanzi.com/2011/02/change-font-size-and-type-of-empathy-in-ubuntu-10-04/)

Because of the changed setup of the website, the right link is: [http://tumutanzi.com/archives/88](http://tumutanzi.com/archives/88)

---

### Post by tumutanzi.com on 2012-05-18
> **akila87 said:**
> Try this link [http://tumutanzi.com/2011/02/change-font-size-and-type-of-empathy-in-ubuntu-10-04/](http://tumutanzi.com/2011/02/change-font-size-and-type-of-empathy-in-ubuntu-10-04/)

Even I myself do not know this link, you are so smart to find this link.
Thanks very much.

---

### Post by foxmuldr on 2012-07-03
If you look in the /usr/share/adium/message-styles/[theme, such as ubuntu.AdiumMessageStyle]/Contents/Resources/ path, you'll find two directories:

Incoming
Outgoing

In those directories are two files:
Content.html
NextContent.html

If you go into those files (open in terminal, "sudo gedit Content.html", etc) and manually insert this before and after %message%

<font face="Tuffy" size="10">%message%</font>

Then you'll have an updated font in whatever face and size you like.  You can add personal coloring as well using the standard #rrggbb (rr=red, gg=green, bb=blue) with color="#rrggbb", new size, etc., which will override everything else.

See this website on various #rrggbb color codes:  [http://www.svpal.org/webhelp/colors.html](http://www.svpal.org/webhelp/colors.html)

Note:  After changing, you'll have to go back in to the edit->preferences->themes and load another theme temporarily, then load back to the theme you just edited, close your chat windows and re-open them for it to take effect.

Note:  Historical entries are already written in the previous format, so they will not be updated. Only new content.

Note:  It's ridiculous that we have to jump through such manual hoops to change things like this.  There should be a "theme editor" standard in Empathy by now (considering how mature the product is).  Very sad and frustrating that there isn't one.

---

### Post by oldos2er on 2012-07-03
Old thread closed.

---

