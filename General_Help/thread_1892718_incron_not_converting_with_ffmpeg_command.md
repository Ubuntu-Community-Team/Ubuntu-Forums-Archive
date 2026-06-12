---
title: "incron not converting with ffmpeg command"
date: 2011-12-08
forum: General Help
---

### Post by groach45 on 2011-12-08
I am trying to set up incron to monitor my Shows folder and whenever a new show is moved to that folder I would like it to convert it.

The incrontab entry is as follows:
```
/home/ubuntu/USB-HD/Shows/Sons\ of\ Anarchy/Season\ 4/ IN_MOVED_TO /usr/bin/ffmpeg -i "$@$#" -vcodec wmv2  -acodec wmav2 -b 1200kb -ab 160kb -r 25 -s 720x480 -v 0 -y "$@Converted/$#.wmv"
```Looking at the /var/log/syslog I see the folloing entry:
```
Dec  8 15:54:06 ubuntu incrond[1098]: (root) CMD (/usr/bin/ffmpeg -i "/home/ubuntu/USB-HD/Shows/Sons of Anarchy/Season 4/Sons.of.Anarchy.S04E14.HDTV.XviD-ASAP.avi" -vcodec wmv2  -acodec wmav2 -b 1200kb -ab 160kb -r 25 -s 720x480 -v 0 -y "/home/ubuntu/USB-HD/Shows/Sons of Anarchy/Season 4/Converted/Sons.of.Anarchy.S04E14.HDTV.XviD-ASAP.avi.wmv")

```As you can see it appears the CMD has been run, but no file appears in the Converted/ folder.

If I copy the command directly from the syslog and paste it into terminal, it runs flawlessly and creates the .wmv file in the Converted/ folder.

So how can I get incron to do the same?

*****Edit********
After hours of trial and error I was finally able to figure this out. The problem has to do with the input file path having spaces in it. When incron was told the watch directory the spaces were proceeded with a backslash as seen in the incron entry above. Incron has no problem with this and watches the directory correctly. The problem is introduced in the directory path wildcard: $@. As you can see above in the syslog it doesn't replicate the backslashes, which is the reason I had initially put quotes around the path. For some reason incron does not use quotes the same way that bash does, which explains why the command worked in the terminal but not in incron. To fix this I just put the paths in manually with the backslashes and stopped using the $@ wildcard all together. The working incrontab entry is as follows: 
```
/home/ubuntu/USB-HD/Shows/Sons\ of\ Anarchy/Season\ 4/ IN_MOVED_TO /usr/bin/ffmpeg -i /home/ubuntu/USB-HD/Shows/Sons\ of\ Anarchy/Season\ 4/$# -vcodec wmv2 -acodec wmav2 -b 1200kb -ab 160kb -r 25 -s 720x480 -v 0 -y /home/ubuntu/USB-HD/Shows/Sons\ of\ Anarchy/Season\ 4/Converted/$#.wmv
```

And the resulting working syslog entry is as follows:
```
Dec  9 11:54:21 ubuntu incrond[1098]: (root) CMD (/usr/bin/ffmpeg -i /home/ubuntu/USB-HD/Shows/Sons\ of\ Anarchy/Season\ 4/Sons.of.Anarchy.S04E14.HDTV.XviD-ASAP.avi -vcodec wmv2 -acodec wmav2 -b 1200kb -ab 160kb -r 25 -s 720x480 -v 0 -y /home/ubuntu/USB-HD/Shows/Sons\ of\ Anarchy/Season\ 4/Converted/Sons.of.Anarchy.S04E14.HDTV.XviD-ASAP.avi.wmv)

```

I still used the wildcard for the file name, $# , but that is because the file I was testing didn't have any spaces in it. This could become a major problem if the naming convention of the file were different. So this issue obviously needs to be addressed within incron. 

Hopefully this helps you brave incron users out there. Incron is a great tool, but does have a few bugs and not a huge support group, as this will be the first solved incron thread on the ubuntu forum. I hope it helps.

---

