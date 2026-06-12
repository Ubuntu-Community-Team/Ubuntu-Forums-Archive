---
title: "Is torrent is better to download an iso"
date: 2010-10-30
forum: General Help
---

### Post by asifnaz on 2010-10-30
I have downloaded iso such as Lubuntu ,xbuntu ,puppy linux , Debian 5 etc .
It is a hit or miss so far . Some cds work other just dont .
I burnt them using minimum speed .
Why torrent download is recommended to download an iso

---

### Post by WorMzy on 2010-10-30
Because it's faster, less drain on servers, and allows you to pause the download and resume it later.

---

### Post by Boondoklife on 2010-10-30
Well it is not necessarily faster, but it does move the load from Ubuntu's servers to individual users which in turn saves them bandwidth and possibly money.

Direct downloads are normally faster for me and with a download manager you can pause downloads and resume them when your ready.

---

### Post by asifnaz on 2010-10-30
> **Boondoklife said:**
> Well it is not necessarily faster, but it does move the load from Ubuntu's servers to individual users which in turn saves them bandwidth and possibly money.

Direct downloads are normally faster for me and with a download manager you can pause downloads and resume them when your ready.
Why was I asked to download iso from torrent when I had errors in cd

---

### Post by CharlesA on 2010-10-30
> **asifnaz said:**
> Why was I asked to download iso from torrent when I had errors in cd

When you download something from a torrent, it checks the file for discrepancies and re-downloads the data that is corrupt.

That ensures that you have a good ISO.

I still verify the sha1sum and md5sum before burning to a cd at something like 4x speed.

---

### Post by nitstorm on 2010-10-30
> > **CharlesA said:**
> When you download something from a torrent, it checks the file for discrepancies and re-downloads the data that is corrupt.

That ensures that you have a good ISO.

I still verify the sha1sum and md5sum before burning to a cd at something like 4x speed.
*LOL, apparently I type slowly :P Still gonna let my comment be*


Well coz a direct download might have some interruptions here and there and u might lose a few bits or something like that here and there ( only very small possibility) but with a torrent download, the torrent downloading client usually hash checks after the download and re-downloads any missing pieces...

if u insist on a direct download without torrents, try 

```

wget -c "the-address-to-the-iso-here"

```

That way even if your direct download gets interrupted, it'll pick up from where it left off...

Hope this was atleast summat useful, if not, excusez moi :)

---

### Post by hawthornso23 on 2010-10-30
In a torrent the pieces are signed and checked. If a piece doesn't verify with its signature it is discarded and redownloaded. A torrent CANNOT be corrupted. This is actually essential because you don't know the people who are sending you the pieces. Only the fact that  the pieces are signed in this way stops people corrupting the process by sending out altered pieces. And people have tried really hard. The music and movie industries would desperately like to find a way to corrupt torrent downloads, but have never succeeded in doing so. Downloads are also checked, but not nearly as rigorously as torrents. I'd trust a torrent more.

The problem you are having is most likely related to the way you write the CD. Use lowest possible speed and don't run any other software while the CD is burning. Also look at the type of blank CD you are using and check that you've got the right type for your CD writer. 

Another option these days is to create a bootable USB key and install off that.

---

### Post by Boondoklife on 2010-10-30
Actually just do an MD5 on the file you downloaded and compare it to the one on:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

if they match then chances are very good you have a good image.

---

