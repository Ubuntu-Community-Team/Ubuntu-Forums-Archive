---
title: "After installing Ubuntu Windows 7 not working"
date: 2011-10-23
forum: General Help
---

### Post by inkerthinker on 2011-10-23
Hey Everyone,

So yesterday I installed Ubuntu dual boot along with my Windows 7 and I have loved Ubuntu! Its awesome but when I needed Windows yesterday it wouldn't boot and when I try to access the built-in system recovery it doesn't work. What do I do. I have a HP-G62 so if you can find a link where I can burn a recovery disk that would be awesome as well. 

-Adithya Sudarsan

---

### Post by raja.genupula on 2011-10-23
> **inkerthinker said:**
> Hey Everyone,

So yesterday I installed Ubuntu dual boot along with my Windows 7 and I have loved Ubuntu! Its awesome but when I needed Windows yesterday it wouldn't boot and when I try to access the built-in system recovery it doesn't work. What do I do. I have a HP-G62 so if you can find a link where I can burn a recovery disk that would be awesome as well. 

-Adithya Sudarsan

[Click please]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00810334&lang=en&cc=us&contentType=SupportFAQ&prodSeriesId=4078809&prodTypeId=321957")

---

### Post by inkerthinker on 2011-10-23
Thanks for the reply! I have a question though will I be able to keep my Ubuntu install while recovering to Windows?

---

### Post by raja.genupula on 2011-10-23
> **inkerthinker said:**
> Thanks for the reply! I have a question though will I be able to keep my Ubuntu install while recovering to Windows?

Hi man , i don't have complete idea about that but take a look that link for that info and look for FAQ's

All the best.

---

### Post by Mark Phelps on 2011-10-23
You don't need to reinstall.  Most probably, since you likely used the Ubuntu installer to shrink the Win7 OS to make room for Ubuntu, is that you got caught by the side-effect of your Win7 OS filesystem being corrupted.

You should have used the Backup feature of Win7 BEFORE you installed Ubuntu to create and burn a Win7 Repair CD. You could have done that for free.

But now, to get the same, you will have to purchase a CD image from the link below:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

After you've downloaded it, burn a CD from it. That will be a Win7 Repair CD.  Boot into that and run Startup Repair three times.

---

### Post by inkerthinker on 2011-10-27
Thanks. I realize I did mess up a little bit. Well I learned from this at least. Will try and get a copy of Windows 7 soon but in the mean time really getting use to Ubuntu so a small plus there :D

---

### Post by oldfred on 2011-10-28
If you post this we can see what is where. A few fixes can be made from Ubuntu or other Linux repairCDs. With XP everything but chkdsk could be done from Ubuntu.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by inkerthinker on 2011-10-29
Alright so I logged on to windows and copied the error code. It was...

```
oxc0000225
```

Any ideas on how I can fix this?

---

### Post by oldfred on 2011-10-29
I do not know windows errors. You can try Google. 

Post boot script and that will tell use something.

---

