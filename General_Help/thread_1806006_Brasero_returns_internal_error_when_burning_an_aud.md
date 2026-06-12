---
title: "Brasero returns internal error when burning an audio CD"
date: 2011-07-17
forum: General Help
---

### Post by vatzec on 2011-07-17
Hey!

I'm trying to burn an audio CD with Brasero. Every time I try this, it fails, but it works when writing to an image file. Brasero quits with the following messages in log:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2862)
```

Do you know what could be causing this?

Thanks!

---

### Post by jerrrys on 2011-07-17
in edit>plugins; configure "cdrdao"

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696/comments/155](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696/comments/155)

---

### Post by vatzec on 2011-07-18
> **jerrrys said:**
> in edit>plugins; configure "cdrdao"

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696/comments/155](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/529696/comments/155)

Thanks for your response!

I have "cdrdao" (the package) installed (Brasero's prompted me to do that upon first attempt to burn the audio CD). I've tried switching the only option available in the cdrdao plugin's configuration box, but it didn't help. I think the plugin isn't working - its entry on Brasero's plugins list is greyed out.

---

### Post by XubuRoxMySox on 2011-07-18
Brasero frequently and randomly made coasters on my machine too! No plugins fixed it, so I just removed it and replaced it with Xburn, which works flawlessly every time. K3B is awesome too, but pulls in lotsa dependencies when it's installed on Ubu or Xubu.

Hope that helps,
Robin

---

### Post by jerrrys on 2011-07-18
yes k3b is a big download (about 300M), but worth it in my opinion...

---

### Post by vatzec on 2011-07-19
Thanks, guys, I'll try to use something else. But it'd be good to have Brasero fixed.

[B]EDIT: One way to work this around is to burn the audio CD to an image file instead of directly to the disc first, and then to burn the image onto the actual CD.

EDIT 2: The problem might be an incompatibility between the versions of cdrdao and brasero in Ubuntu repositories. Another great (and simple!) CD/DVD burning program I have found is called Xfburn.[/B]

---

