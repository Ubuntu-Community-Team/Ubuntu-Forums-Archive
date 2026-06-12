---
title: "Deluge. Upload problem."
date: 2009-09-13
forum: General Help
---

### Post by vvp86 on 2009-09-13
I can download something with deluge. But upload speed is always 0. BTW there are a lot of peers. No one can get something from me. I don't have firestarter or something. I have DLink router and tried to setup port forwarding - it din't help. Could someone help me please?

---

### Post by harrismh777 on 2009-09-13
First step when you have network problems is ping.

Can you ping out...   can others ping back.


can you ping a known user on your local subnet... on the internet?

Can others ping your machine on the local subnet... from the internet?

---

### Post by lovinglinux on 2009-09-13
> **vvp86 said:**
> I can download something with deluge. But upload speed is always 0. BTW there are a lot of peers. No one can get something from me. I don't have firestarter or something. I have DLink router and tried to setup port forwarding - it din't help. Could someone help me please?

Port-forwarding has nothing to do with upload/download but with the number of peers you connect to. See a better explanation at [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

Would be nice if you could provide more info like:

- Have you configured Deluge upload speed correctly?
- Do you have other torrents active while downloading?
- Does the torrent upload speed stays at zero even when you are still downloading it or only when you are trying to seed it?

Also, it could be your ISP blocking the upload. I'm not sure if it would be possible to download in this scenario, but some ISP completely blocks seeding.

---

### Post by vvp86 on 2009-09-13
I can ping anybody and can be pinged. Speedsettings is allright. I tried to seed with active torrents and without. I cannot seed. My provider definitely doesn't block torrents. Upload speed stays at zero anytime :(

---

### Post by lovinglinux on 2009-09-13
> **vvp86 said:**
> I can ping anybody and can be pinged. Speedsettings is allright. I tried to seed with active torrents and without. I cannot seed. My provider definitely doesn't block torrents. Upload speed stays at zero anytime :(

An active torrent is one that is currently not paused, so it will be uploading (seeding) or downloading + uploading. So, the torrents with zero upload speed are active and downloading (the file is not completed yet) or just active but not seeding (file is already completed)? Have you checked if the torrent has connected peers? Have you checked if the tracker is responding? 

Keep in mind that problems can be isolated to single torrent files. So does this happens with all torrents you set as active?

---

### Post by vvp86 on 2009-09-14
Files are already downloaded. Deluge shows that there are more than 4000 peers who want to download it too. But they cannot connect to me. So upload speed is 0. Torrents are not paused. Tracker is active. It happens with all torrents.

---

### Post by vvp86 on 2009-09-14
May be i setup my router incorrect way?? I tried to setup just port forwarding. But as i said i didn't help.

---

### Post by lovinglinux on 2009-09-14
> **vvp86 said:**
> Files are already downloaded. Deluge shows that there are more than 4000 peers who want to download it too. But they cannot connect to me. So upload speed is 0. Torrents are not paused. Tracker is active. It happens with all torrents.

> **vvp86 said:**
> May be i setup my router incorrect way?? I tried to setup just port forwarding. But as i said i didn't help.

Visit the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923) for instructions on how to properly configure port forwarding. It also has a Troubleshooting section, with instructions on how to test it. I have finished the tutorial yesterday.

It could be a closed port, but also could be your ISP preventing you from seeding. I don't remember which ISP do that, but I know they can do it. They can prevent you from seeding completely. Nevertheless, you should try to open the port properly.

---

### Post by Kongu on 2010-12-06
I know this thread is a year old, but I had the same problem with Deluge not seeding and I couldn't find the answer anywhere, so I'm putting my solution here in case other people might have the same problems in the future:

Preference -> Queue -> Tick: Do not count slow torrents

Now, it's uploading full-steam.

---

### Post by Nitronium on 2012-01-18
That's it! Kongu, thanks! What you did in replying to a year old thread with that info helped me :-) Many thanks :-)

---

