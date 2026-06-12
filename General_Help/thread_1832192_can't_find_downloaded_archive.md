---
title: "can't find downloaded archive"
date: 2011-08-24
forum: General Help
---

### Post by pboat on 2011-08-24
Hi,
I'm using Ubuntu 10.10, which comes with FF 3.6. I wanted to update to the latest stable version, so I went ahead and downloaded the tar.gz file directly from the Mozilla website. I chose the option "open with archive manager", which caused the Archive Manager to open once the download was complete. Then I was filled with questions like "Where should I extract the archive", "Is there an installation process", etc. With some Googling, I discovered that I could install the latest version of FF within the software manager by updating the software sources and then using the Update Manager. This worked great, and now I have FF 6 installed. 

However, I still have the Archive Manager opened with the downloaded FF tar.gz folder, and I would now like to delete this archive, but there doesn't seem to be an option in the Archive Manager to do this. When I clicked on the archive properties, it listed the archive's location as "file:///tmp". I'm not exactly sure what that refers to, but I went to /tmp, I couldn't find the archive there. I also looked in /var/cache/apt/archives, and there are several firefox related archives, but I'm not sure if any of those are related to the archive I just downloaded (they all have .deb extensions, not .tar.gz extensions). Does anyone know where the archive manager downloads these archive files?
Thank you

---

### Post by skinnyquiver on 2011-08-24
> **pboat said:**
> Hi,
I'm using Ubuntu 10.10, which comes with FF 3.6. I wanted to update to the latest stable version, so I went ahead and downloaded the tar.gz file directly from the Mozilla website. I chose the option "open with archive manager", which caused the Archive Manager to open once the download was complete. Then I was filled with questions like "Where should I extract the archive", "Is there an installation process", etc. With some Googling, I discovered that I could install the latest version of FF within the software manager by updating the software sources and then using the Update Manager. This worked great, and now I have FF 6 installed. 

However, I still have the Archive Manager opened with the downloaded FF tar.gz folder, and I would now like to delete this archive, but there doesn't seem to be an option in the Archive Manager to do this. When I clicked on the archive properties, it listed the archive's location as "file:///tmp". I'm not exactly sure what that refers to, but I went to /tmp, I couldn't find the archive there. I also looked in /var/cache/apt/archives, and there are several firefox related archives, but I'm not sure if any of those are related to the archive I just downloaded (they all have .deb extensions, not .tar.gz extensions). Does anyone know where the archive manager downloads these archive files?
Thank you

you could use locate to search your system for the files
sudo updatedb
locate (filename of one of the firefox files)

---

### Post by pboat on 2011-08-24
@skinnyquiver: hi, thanks. I did what you said, but it didn't show up the archive. I searched for "firefox-6.0.tar.bz2" and nothing came up. Then I searched the simpler string "firefox", and lots came up, but not the downloaded archive. Any other suggestions? Thanks.

---

### Post by skinnyquiver on 2011-08-30
> **pboat said:**
> @skinnyquiver: hi, thanks. I did what you said, but it didn't show up the archive. I searched for "firefox-6.0.tar.bz2" and nothing came up. Then I searched the simpler string "firefox", and lots came up, but not the downloaded archive. Any other suggestions? Thanks.

If it did not find it it is most likely not on your system the Archive Manager probably just has it cached in memory

---

