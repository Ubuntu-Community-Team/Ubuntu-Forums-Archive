---
title: "Missing directories"
date: 2011-03-26
forum: General Help
---

### Post by Jynxed on 2011-03-26
Hey, I've been using Ubuntu for several months now, verging on a year. Twice I have had folders completely disappear from my computer. First is was a music folder /home/name/Music and I figured that I accidentally deleted it myself, even though it wasn't in the trash, and I could find no evidence of it anywhere. This time it's my /home/name/Downloads folder, which had a lot more things that I would consider 'important' to some degree.

My laptop is 3 years old now, and has issues with overheating.

Does anyone have any idea if there might be a way to recover these files? If not, is there something I can do so that I can recover them in the future?

Thank you very much.

---

### Post by s3MA00RRNY on 2011-03-26
DO NOT CLICK THE LINK FROM u3untu, IT'S ADVERTISING!

---

### Post by newbuntuxx on 2011-03-26
Either your hard drive is dying or someone else has access to your machine.

---

### Post by jerome1232 on 2011-03-26
> **newbuntuxx said:**
> Either your hard drive is [COLOR="Red"]dying[/COLOR] or someone else has access to your machine.


Can you pull up Disk Utility, tell it to run smart tests and see if your disk is in fact dying? You might need to get a replacement ***very*** soon, and backup your data if it is.

---

### Post by linuxuser12345 on 2011-03-26
Reinstall, reinstall, reinstall!
If you doo need a new hard drive though, DO NOT buy one from the store! They are overpriced!

Go to [www.newegg.com]("http://ubuntuforums.org/www.newegg.com") and buy one there. You can get a 500GB Hard Drive for $38.00

---

### Post by Jynxed on 2011-03-27
Disk check utility comes up empty, but the internal temperature is 100*F.

There is no one else with physical access to my machine, and I have no reason to believe that I got a virus, since there is nothing else behaving oddly, my computer is not running slow, and it is only one single directory that is missing.

---

### Post by newbuntuxx on 2011-03-27
if you know the contents of the directory, maybe you can try to search for them:

open terminal and run:

```
sudo find / -iname *\.ext
```

Where "ext" is the file extension.(* specifies 0 or more characters,\ escapes the .) 

If you remember some of the file names, you can search for them like this:

```
sudo find / -iname "filename"
```

Or if you remember a portion of the filename, then you can use *:

```
sudo find / -iname "*filename*"
```

You can of course restore deleted files from your disk. I think the easiest way is to download: [http://www.redobackup.org/](http://www.redobackup.org/), burn it on cd, and boot from it. 

I think it has an option to search for deleted files with certain extensions, like pictures, or audio etc....

Download it, burn it, boot from it. And let us know how it goes :)

---

### Post by gordintoronto on 2011-03-27
> **Jynxed said:**
> Disk check utility comes up empty, but the internal temperature is 100*F.


That's a very reasonable temperature. If it were 100C, that would be different. Is that temperature from hddtemp?

---

