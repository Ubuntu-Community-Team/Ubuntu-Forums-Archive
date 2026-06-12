---
title: "need help installing"
date: 2011-03-04
forum: General Help
---

### Post by Ali.A on 2011-03-04
something weird happened to my windows xp and now i can't access it.

and i thought about downloading Ubuntu (which i already did) and then when i tried booting from the CD .. an error came up and i don't know why it's doing that. :o :(

i downloaded it properly and legally too.... i don't know why i can't replace windows xp and install Ubuntu as my main OS


thanks for any help in advance :)

please help quickly i kinda need work to finish on computer and it's due tomorrow

---

### Post by spiky001 on 2011-03-04
Did you change the bios of the computer to boot from cd? What error did you get when you tried to install

---

### Post by Ali.A on 2011-03-04
yes i did change bios to boot from cd

and the error is:

[COLOR="Red"]BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Can not mount /dev/loop0/ (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs[/COLOR]

and then after a little while this comes up:

[COLOR="red"]udevd[85]: worker [196] unexpectedly returned with status 0x0100

udevd[85]: worker [196] failed while handling '/devices/virtual/block/loop0'[/COLOR]

---

### Post by grahammechanical on 2011-03-04
You do not tell us the error message or what it was that was weird about XP. You may have a serious hardware failure that would stop any operating system from running.

Regards.

---

### Post by wiggly81 on 2011-03-04
did you check the MD5 sum of the downloaded Ubuntu iso file? it is common to download the image and have a problem with the downloaded file, it is always advised that you check that MD5 sum of the image before you burn the CD the best way to download the image files is via torrent as the clients generally check for errors while downloading and any bad data is dropped and replaced with the good data.

read this
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and this
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by spiky001 on 2011-03-04
Did you run a md5 sum check on disk? burn disc at slowest speed can you run Ubuntu as live cd

---

### Post by Ali.A on 2011-03-04
no i don't have a serious hardware failure,, it's just that when i tried to run the demo version or the full version of Ubuntu it doesn't work

and can you just tell me how to fix this instead of telling me what tell you or not

i have serious work to finish and i need help fast

---

### Post by spiky001 on 2011-03-04
We are telling you how to fix, but a few things need to be checked I,E md5sum you may have a bad copy of disc. It should load as a live cd which means it wont change the machine setup, so until yo can confirm the disc is ok that might be where the problem is

---

### Post by Ali.A on 2011-03-04
can anyone tell me how to check the MD5 sum of the download iso file in SIMPLE words because i am really confused by the way the HowToMD5SUM tells me

and how do you get to the downloaded Ubuntu iso file 

(what is an iso file anyway??
sorry i am kinda new in all these stuff)

---

### Post by spiky001 on 2011-03-04
You said you have downloaded ubuntu. What have you downloaded? What os System are you using now???

---

### Post by wiggly81 on 2011-03-04
iso files are basically CD/DVD's without the disc this makes them able to be shared over the internet then burned to a blank disc.

what operating system are you using at the moment as checking the MD5 sum is different on different systems

[http://www.ubuntu.com](http://www.ubuntu.com) this is where you will find the downloads for Ubuntu.

---

### Post by Ali.A on 2011-03-04
oh.. so an iso file is the zipped file i downloaded???

i downloaded Ubuntu 10.10

and i am using my sisters laptop which has windows 7 currently 

but i want to put it on my computer that needs an operating system

---

### Post by spiky001 on 2011-03-04
It,s not a zipped file it should have an extension .iso That needs to be burnt to disc at slowest speed then yo can boot of that as a live cd

---

### Post by wiggly81 on 2011-03-04
bare in mind on windows things like winrar/winzip open .iso files and show the same icon for zip / rar / iso and windows does not tend to show the extension so it could look like a zip file to a windows user

---

### Post by Ali.A on 2011-03-04
ok then i will try erasing everything and burn it again but at slow speed

by the way how do you burn it at slow speed??

because when it was burning the speed was 4x

---

### Post by spiky001 on 2011-03-04
> bare in mind on windows things like winrar/winzip open .iso files and  show the same icon for zip / rar / iso and windows does not tend to show  the extension so it could look like a zip file to a windows userI didn't know that thks wiiggly

A link for md5 in win7 [http://helpdeskgeek.com/how-to/check-md5sum-in-windows-7/](http://helpdeskgeek.com/how-to/check-md5sum-in-windows-7/)

---

### Post by Ali.A on 2011-03-04
my sisters laptop doesn't have an option to burn at less than 4x speed

---

### Post by spiky001 on 2011-03-04
I,ve done mine  at 4 worked ok

I would advise checking md5

---

### Post by wiggly81 on 2011-03-04
> **spiky001 said:**
> I didn't know that thks wiiggly

no problem i have not long ago left windows to stick 100% with ubuntu so i still have some windows blood in me lol

4x is most likely the lowest for most people these days and should be fine but it is always very important to check the MD5 as it gets frustrating trying to install a system to find errors halfway through

---

### Post by Ali.A on 2011-03-04
can you guys just tell me how to check md5 in your own words and in the most simple way

i am really getting frustrated by this md5 thing and the link wiggly gave my was to confusing to understand

---

### Post by wiggly81 on 2011-03-04
we need to know the exact file name of the downloaded iso...

it will be somthing like
ubuntu-10.10-desktop-amd64.iso

then we can find the correct MD5 hash for you

download this as spiky suggested
[http://downloads.sourceforge.net/portableapps/winMd5SumPortable_1.0.1.55_Rev_3_English.paf.exe?download](http://downloads.sourceforge.net/portableapps/winMd5SumPortable_1.0.1.55_Rev_3_English.paf.exe?download)

it is a simple bit of software to get the MD5 hash of the downloaded iso

---

### Post by spiky001 on 2011-03-04
md5sum checks that the file you downloaded is as it should be exactlly I hope wiggly has a good link  for win md5 checking there will be a number supplied with your download you can check with the original version

Here are the md5sums of 10.10 just check against the version you are using  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by Ali.A on 2011-03-04
thanks
and my iso is .... ubuntu-10.10-desktop-1386.iso

---

### Post by wiggly81 on 2011-03-04
ok then the number you need to have returned by the MD5 check software is 
```
59d15a16ce90c8ee97fa7c211b7673a8
```
if the number does not match exactly then the iso is corrupt and you will need to download it again and recheck it

---

### Post by spiky001 on 2011-03-04
59d15a16ce90c8ee97fa7c211b7673a8 this is the md5sum

---

### Post by Ali.A on 2011-03-04
how do i check what my md5 is???

---

### Post by Ali.A on 2011-03-04
i opened my md5sum as notepad and this is what i see:


8606bee30b5fc55cb9c9a8f997607552  ./casper/initrd.lz
3e98978b3ca88f55dbc92fedbdd186ab  ./casper/filesystem.manifest
64dd1323213448e9e3e42e3b639d5fa3  ./casper/filesystem.manifest-desktop
49c84ad768c39cdf140061a61a428079  ./casper/filesystem.squashfs
50065155d2b4c37740b0e123cbfebc43  ./casper/vmlinuz
a13b7e99c829f41ddb89fcf20780fb1d  ./casper/filesystem.size
4f06aa578751899c1c43dde93164b0ce  ./dists/maverick/Release
5a9313d8543fea359656a1b08b411461  ./dists/maverick/restricted/binary-i386/Packages.gz
2f88764d78ab5a3101c5ed72f7f79d6c  ./dists/maverick/restricted/binary-i386/Release
dd7fd3b7cd349117f720654019f14922  ./dists/maverick/Release.gpg
81297d08599b2b2276dcf94f8c9543e3  ./dists/maverick/main/binary-i386/Packages.gz
b073e6f461e2d54143f70b3d40f57636  ./dists/maverick/main/binary-i386/Release
461cbc7ff94fdea8008cab34b611abb8  ./pics/blue-upperright.png
cd8aa5e7fa11b1362ef1869ac6b1aa56  ./pics/blue-lowerleft.png
a025c46d5daf227adfda51d81eb90f25  ./pics/blue-upperleft.png
92091902d3ca753bb858d4682b3fc26b  ./pics/logo-50.jpg
3c129ee10f707bd9dec10209d28840eb  ./pics/red-upperright.png
cde56251d6cae5214227d887dee3bab7  ./pics/red-upperleft.png
20d4bdecfa6d980d663fb5b93d37a842  ./pics/red-lowerright.png
0730e775a72519aaa450a3774fca5f55  ./pics/red-lowerleft.png
16ff51c168405e575d32bae001f280e4  ./pics/debian.jpg
9e18ae797773b2677b1b7b86e2aff28d  ./pics/blue-lowerright.png
c1a1595f9949c3d2d5fb22a525c26d7c  ./.disk/casper-uuid-generic
0d1f47b5bc3e4d762bc59581a766eeaf  ./.disk/release_notes_url
728cb968a88534e0c50a9d99621f13eb  ./.disk/cd_type
d41d8cd98f00b204e9800998ecf8427e  ./.disk/base_installable
7fd5ba45aa3d361369e7c15914c73bc2  ./.disk/info
62bf7841341b7faa69062fd0095af116  ./autorun.inf
8d6a2a045d7c0f48fe2e088f3f87b6ce  ./install/README.sbm
5a93a111efeb5305075c5e077715b6cd  ./install/sbm.bin
597df07bd94c2844aade36c28a7d421f  ./install/mt86plus
fe6fa04c981a9d3835f12f27bd6dda71  ./usb-creator.exe
24ec176894c781355f9ccb08ba69919e  ./preseed/ubuntu.seed
0391854d1af5a015a667f29fa0442e78  ./preseed/ltsp.seed
7e3aa6d1958baf72d369392fdb175486  ./preseed/cli.seed
6b711ba074b35f57ff4cb4c453109709  ./pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
d21ce544f70c9c7d6a3af452d3e4b7c3  ./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20100718-2_i386.deb
e8db25137962d97309baf051a7e66f7b  ./pool/main/n/ndisgtk/ndisgtk_0.8.5-1_i386.deb
1cb737e6d019f35cc5e4664e5b5db265  ./pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.56-3_i386.deb
74524f0ecc162d0f89f999ef832c99aa  ./pool/main/n/ndiswrapper/ndiswrapper-common_1.56-3_all.deb
561b1be68e99e1c7c9e6664fb6e87e81  ./pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-1_all.deb
5cf3364130a9e9b11d71deadb0354648  ./pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.02-1_all.deb
96e9bf35608b3380ca8dc6920255de3b  ./pool/main/b/build-essential/build-essential_11.5_i386.deb
a3279e18d400c54047b49853462d02b4  ./pool/main/b/b43-fwcutter/b43-fwcutter_013-2_i386.deb
3b4bb5a8f62636fd45480eecbe0520ea  ./pool/main/d/dpkg/dpkg-dev_1.15.8.4ubuntu3_all.deb
0708808b66daffa5520d270d76151417  ./pool/main/d/dpkg/libdpkg-perl_1.15.8.4ubuntu3_all.deb
bd0c1ef87e2466d74ea6ac42755ea29e  ./pool/main/d/dkms/dkms_2.1.1.2-3ubuntu1_all.deb
67259128a0d7c83e7c7b56e270a0741e  ./pool/main/g/gcc-4.4/libstdc++6-4.4-dev_4.4.4-14ubuntu5_i386.deb
09411ea75687bac8174dc18c65570547  ./pool/main/g/gcc-4.4/g++-4.4_4.4.4-14ubuntu5_i386.deb
4e3190bd7e336e9640cc643118e43a2b  ./pool/main/g/gcc-defaults/g++_4.4.4-1ubuntu2_i386.deb
308563b2eb5f6a64ead0a3b81afa4c66  ./pool/main/u/ubiquity/oem-config_2.4.8_all.deb
4a868215dc22264a78983d70fb9f73d6  ./pool/main/u/ubiquity/oem-config-gtk_2.4.8_all.deb
f8b821c5b94f3f06c779124959a47db2  ./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu7_i386.deb
1b8a459712dd9a5a9b3aecd16a8219ab  ./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-1ubuntu1_i386.deb
a3507aa839e3a0a2d1bc4e01109b3f62  ./pool/main/w/wvstreams/libuniconf4.6_4.6.1-1ubuntu1_i386.deb
f5c6ff1c251dff34531fa4a9c91da08a  ./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-1ubuntu1_i386.deb
756a6e5677184e1276094dd9cb0af9db  ./pool/main/w/wvdial/wvdial_1.60.4_i386.deb
4d4d776758c9d1535b486000ff673eff  ./pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb
80ca9c983f402d6dddb02c4d7c1b27c4  ./pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb
90728e63cba4cbc65d0d653ab400d164  ./pool/main/l/linux-wlan-ng/linux-wlan-ng_0.2.9+dfsg-4_i386.deb
3aafaec3951819c3e353e6fd635bc289  ./pool/main/l/linux-wlan-ng/linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb
67169557c4c6fe5ea454057af102a8e4  ./pool/main/l/lupin/lupin-support_0.32_all.deb
cb3d5b5de9f45e5a107131c7230679f9  ./pool/main/s/setserial/setserial_2.17-45.2ubuntu2_i386.deb
bf8d2e9369530a8a22a92fa6ee59f9ce  ./boot/grub/loopback.cfg
d1db1f93bb7486593b7d1ea023c0e3f8  ./wubi.exe
481889d4a0b3b43b83636a4a7a28dab0  ./README.diskdefines

---

### Post by wiggly81 on 2011-03-04
download the software we have given a link to it, then it will ask you what file you want to check, browse to your downloaded iso file and check it

---

### Post by Ali.A on 2011-03-04
i used the software and the results are the same

now what do i do

---

### Post by wiggly81 on 2011-03-04
now you can burn the iso file to CD and it should run fine

---

### Post by Ali.A on 2011-03-04
do i just copy the iso file into the disc

or

should i extract it to the disc

---

### Post by wiggly81 on 2011-03-04
depending on the software you are using to burn the image there should be an option "burn image to disc" or somthing along the lines of that, if you extract the data and burn it it will most likley not boot also if u just burn the .iso file to disc it will not boot you need to make a copy of the contents only.

this should give you extra help..
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Ali.A on 2011-03-04
when i tried burning the disk then at the verifying part an error came up:

[COLOR="Red"]The disk image didn't burn successfully because an error occurred. (Error code: 0x80004005)[/COLOR]

can you help me fix this problem 

by the way i downloaded this right of the Ubuntu website so it should work
but i don't know why it isn't

---

### Post by wiggly81 on 2011-03-04
the error is not related to the iso, it is an error that was created while burning the iso to disc, it was either a 1 off problem in which case just try burning the disc again with a new blank cd (there is no limit to how many times you can burn an iso to disc) if that still gives an error i would check the software you are using to burn the iso, it could be that you need to re-install the burning software.

---

