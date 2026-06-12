---
title: "[HOWTO] Epson CX7800 scanner function"
date: 2010-10-02
forum: General Help
---

### Post by slooksterpsv on 2010-10-02
I had trouble, and have seen others have had trouble, in getting the Epson CX7800 series to scan on their computer, so I've put together a small short guide to help. So here it goes:

1. Go to: [http://avasys.jp/eng/linux_driver/download/](http://avasys.jp/eng/linux_driver/download/) and click on Scanner (even though it's an all-in-one we're clicking Scanner).

2. In the next area it has you select some values so select:
Expression 1600
Distro: Ubuntu
Version: Your version (mine was 10.04 64-bit so I did 10.04)
Country: You decide
Connection Environment: I used local as I'm connecting USB
Product: Individuals (Graphics/Imaging)

3. Now on the page there's 2 things we're going to download (not sure if the one is necessary or not):
```

iscan-data_1.3.0-2_all.deb
iscan_2.26.0-3_amd64.deb (for 64-bit) 
or
iscan_2.26.0-3_i386.deb (for 32-bit)

```
4. Now go ahead and install the iscan-data, it will have to install some other dependencies so let it do so.

5. Now when you try to install iscan it'll tell you you need libltdl3 - so let's download that as a deb, go to: 
[http://packages.ubuntu.com/hardy/libltdl3](http://packages.ubuntu.com/hardy/libltdl3)
Select your version (32-bit or 64-bit), then select a mirror like mirror.kernel.org or that. After that downloads, install it.

6. Now install iscan_2.26...deb. Phew, almost done here.

7. Now if you try to run Imagescan from Applications or in terminal, it fails to find the epson, so here's what I had to do. I had to run:
```

sudo iscan

``` to get it to load up to where I could scan images.

You can also modify the menu at the top to run gksudo iscan
Hope this helps anyone who's had troubles getting the Epson CX7800 scanner function to work.
Let me know if this did or didn't work for you.

Issues: When you scan images, root:root will be the owner of the images. You can change this in terminal by using the chown command.

---

