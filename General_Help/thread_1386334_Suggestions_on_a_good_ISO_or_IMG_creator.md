---
title: "Suggestions on a good ISO or IMG creator?"
date: 2010-01-20
forum: General Help
---

### Post by JiuJitsu500 on 2010-01-20
Hello again! 

I had a strange curiosity... I'd only used a couple ISO creator (rip the image form disk type o' thing) apps, like AcetoneISO and liked it.... but would anyone have another suggestion on a better program?

---

### Post by bulletxt on 2010-01-21
Better, what do you mean? What features do you need?

---

### Post by JiuJitsu500 on 2010-01-21
Easier to use I guess.... Creating ISO's from a disk seemed to be a pain in the backside and would never work when I tried them in virtualbox.... though I didn't exactly use a legitimate Microsoft Windows 7 disc (I'm in Iraq so piracy isn't even a word).... But it still should've worked if it installed on two computers.

As far as I could tell it was odd to burn ISO's back onto a blank disc.

Perhaps I mean a more graphical way? My friend had the same issues... we're both just looking at alternatives. If not, I'll stick to Acetone, it's a very good program.

---

### Post by falconindy on 2010-01-21
dd can do this for you:
```
dd if=/dev/cdrom of=/path/to/cdimage.iso bs=1M
```
You could make this into a bash function...
```
makeiso () {
  dd if=/dev/cdrom of="$*" bs=1M
}
```

And then add this to your ~/.bash_aliases. Then, to make an iso, you'd only have to open a prompt and type "makeiso nameofimage.iso".

---

### Post by bulletxt on 2010-01-21
> **JiuJitsu500 said:**
> Easier to use I guess.... Creating ISO's from a disk seemed to be a pain in the backside and would never work when I tried them in virtualbox.... though I didn't exactly use a legitimate Microsoft Windows 7 disc (I'm in Iraq so piracy isn't even a word).... But it still should've worked if it installed on two computers.

As far as I could tell it was odd to burn ISO's back onto a blank disc.

Perhaps I mean a more graphical way? My friend had the same issues... we're both just looking at alternatives. If not, I'll stick to Acetone, it's a very good program.

Of course I would suggest to use AcetoneISO, nothing more simple. About Windows 7, that's because it's an UDF file system. I think AcetoneISO doesn't correctly support making images of an UDF disc. It's also unable to mount UDF images.

---

### Post by JiuJitsu500 on 2010-01-21
Well.... I didn't expect such great answers :) I like the Bash idea and using dd.... I think I'll have to try this out in a little while. I got those commands saved in a document now... sweet... And the file made.

And I though Acetone would be what most suggest, I'd probably do the same. It is damn easy after all. Thanks for the replys to both of you!

And as for UDF, any way to convert it to something usable in virtualbox? I don't need it, but it would definately be cool... I have Windows XP Vienna concept in one, and not everyone likes it. Like 3 people I think want iTunes on their boxes (because of the lack of support for all the phones and touches coming out).... And Zune is too easy, but if there were an app for Zune I'd like to know.... even if installing a linux-based software on it would do the trick (though I do NOT want to lose my music, I already deleted my whole external hard drive on accident)....

---

### Post by bulletxt on 2010-01-21
> **JiuJitsu500 said:**
> Well.... I didn't expect such great answers :) I like the Bash idea and using dd.... I think I'll have to try this out in a little while. I got those commands saved in a document now... sweet... And the file made.

And I though Acetone would be what most suggest, I'd probably do the same. It is damn easy after all. Thanks for the replys to both of you!

And as for UDF, any way to convert it to something usable in virtualbox? I don't need it, but it would definately be cool... I have Windows XP Vienna concept in one, and not everyone likes it. Like 3 people I think want iTunes on their boxes (because of the lack of support for all the phones and touches coming out).... And Zune is too easy, but if there were an app for Zune I'd like to know.... even if installing a linux-based software on it would do the trick (though I do NOT want to lose my music, I already deleted my whole external hard drive on accident)....

To make an iso of Windows 7, try this command:

genisoimage -udf -J -o windows7.iso /Path_to_Mounted_Windows7_Cdrom


On a default system it should be,

genisoimage -udf -J -o windows7.iso /media/cdrom


Please keep in mind genisoimage support to UDF filesystem is labeled as ALPHA status.

---

### Post by bolucpap on 2010-01-21
How about K3B?

---

### Post by bulletxt on 2010-01-21
> **bolucpap said:**
> How about K3B?

K3B uses mkisofs/genisoimage as backend. Exactly like AcetoneISO.

---

### Post by JiuJitsu500 on 2010-01-21
Sweet.... so I'll stick with Acetone after all :) and those crazy commands.... I will try both to see if I can get a bootable version for sure...

How about Windows XP now though, I have an XP Black DVD... how would this come out? The Vienna works great so I think Black should too.... but I don't know :)

---

