---
title: "FISH in Konqueror"
date: 2006-05-07
forum: General Help
---

### Post by jonnymccullagh on 2006-05-07
I moved from SUse to Kubuntu a few months back and I have been struggling to connect to a linux server I use. On windows I could use WinSCP and on Suse I used the fish:// protocol but fish:// does not seem to work on kubuntu as all I get is:
An error occurred while loading fish://root@111.111.222.222:

Am I missing something?
Thanks,
jonny

---

### Post by cgjones on 2006-05-07
I think you can do the following and get the same results, although I've never used fish before.
```
sftp://*username*@*hostname*
```

---

### Post by jonnymccullagh on 2006-05-08
Thanks - that works well enough but I think using Fish on Suse was a little better but only marginally - thanks,
jonny

---

### Post by xtacocorex on 2006-05-08
What version of Kubuntu are you running? 

I have Breezy and fish works fine for me. I don't include the username in my address. 

Do you also have the kdebase-kio-plugins package installed?

---

