---
title: "Querying folder contents in Conky"
date: 2010-05-16
forum: General Help
---

### Post by marrabld on 2010-05-16
Hi I am using Conky to display my HDD usage and iPod usage using the following in my conkyrc file

```
${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
iPod $alignc ${fs_used /media/IPOD} / ${fs_size /media/IPOD} $alignr ${fs_free_perc /media/IPOD}%
${fs_bar /media/IPOD}
```

It works fine, but the problem I have is, if I disconnect my iPod, the /media/IPOD folder disappears and I end up with a blank fs_bar.

What I would like to do is, check the contents of /media and then display all of the folders in there.  That would extend the fs_bars to display USB drives when I plug them in. 

I am familiar with Python, albeit a little clumsy.  I could probably knock up a quick Python script to return all the folders in /media using 'os.listdir' but I am not sure how to get conky parse the return argument.  Or if that is even the correct approach.  

A nudge in the right direction would be appreciated.

Cheers

[EDIT]

Ok I am a step closer

I missed the if_existing variable described here [http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

So I have updated my conkyrc file to 

```
${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}${if_existing /media/IPOD}
iPod $alignc ${fs_used /media/IPOD} / ${fs_size /media/IPOD} $alignr ${fs_free_perc /media/IPOD}%
${fs_bar /media/IPOD}${endif}
```

Which works great.  Only problem now is, that method only works if I know what the device is mounted as.  My iPod is always mounted to /media/IPOD  but I have about 5 different usb drives that get called different things.  

So I am still curious how to scan the /media folder for mounted files and parse them to conky.

Cheers

---

