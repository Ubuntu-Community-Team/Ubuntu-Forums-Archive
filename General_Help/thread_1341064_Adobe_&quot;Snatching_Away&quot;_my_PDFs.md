---
title: "Adobe &quot;Snatching Away&quot; my PDFs"
date: 2009-11-29
forum: General Help
---

### Post by bradley002 on 2009-11-29
Okay, weird title, weird situation.

I tried to install Adobe Reader through Wine but it crashes when I open it. I don't want to use it anymore. When I double click on a PDF the default viewer is Evince, which is what I want. But an engineering program I use needs to switch to PDF files a lot and when I try to view them it always triggers Adobe Reader instead of Evince.

How can I stop Adobe Reader from "claiming" them?

---

### Post by scouser73 on 2009-11-29
Why are you using Adobe Reader through WINE?
There is a version for Ubuntu.

**1** - Go to the [[COLOR="Red"]**Adobe Reader Website**[/COLOR]]("http://get.adobe.com/uk/reader/?promoid=BUIGO")
**2** - Click on **Different Language Or Operating System**
**3** - Click on the **Select An Operating System** drop down menu
**4** - Select **Linux - x86 (.deb)**
**5** - Click **Continue**
**6** - Select **Adobe Reader 9.2** & Click **Download Now**

That will start installing Adobe PDF Reader for you, once installed you can find it in the Office menu.

---

### Post by bradley002 on 2009-11-29
Actually I think I tried installing the linux version and a version through Wine and neither works. I just want to get rid of them so they don't keep interfering. How can I do that?

---

### Post by The Cog on 2009-11-29
Right-click on a PDF icon, choose Properties and Open With. Set the program you want to be the default opener there.

---

### Post by bradley002 on 2009-11-29
Already set to Evince.

---

### Post by The Cog on 2009-11-29
Is it the "engineering program" that is trying to open the PDF, or are you trying to open it with nautilus?

If it's the engineering program that's trying to open the PDF, is that running native in Linux or in wine? If it's in wine, I don't see any way it could launch evince.

---

### Post by bradley002 on 2009-11-29
ohh, the eng. program is running through Wine, and it is trying to open the PDF's directly.

So anything running through Wine cannot call up non-Wine programs? Does this mean I need to get Adobe Reader working through Wine in order for my program to open the PDFs?

Thanks.

---

### Post by The Cog on 2009-11-29
Hmm. I'm not saying there is no way for a wine program to launch a Linux program, but I'm having difficulty imagining how it could. You need someone with more knowlege of wine than I have. It might be possible.

P.S.
[http://wiki.winehq.org/FAQ#head-68d921c50355f280a905e3574b7dda58d76ff51f](http://wiki.winehq.org/FAQ#head-68d921c50355f280a905e3574b7dda58d76ff51f)

---

