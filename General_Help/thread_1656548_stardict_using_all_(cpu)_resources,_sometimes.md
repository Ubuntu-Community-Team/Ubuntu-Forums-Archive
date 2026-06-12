---
title: "stardict using all (cpu) resources, sometimes"
date: 2010-12-31
forum: General Help
---

### Post by thaitang on 2010-12-31
hi,

I just recently upgraded to 10.04 (LTS), and I have been using stardict app for a long time with nothing but success on each of my laptops anc omputers I have had over the past 5 or so years. However, now on one laptop after starting the stardict app, using panel the applet I create on my xfce4-panel (as per normal), and looking up a word (highlight and press shift key which i use for quick word search using stardict), the app begins using 100% cpu resources and I am forced to kill the process.

The problem is intermittent, meaning it only occurs half of the time I am using startdict, while the other half of the time it operates normally. I have been trying to see if there is some sort of pattern, perhaps other apps running at the time the problem occurs, but I have not noticed anything that looks suspect, since I generally fire up stardict after boot in and have had it happen (the problem) without even any other apps open (just testing to try and find some sort of pattern to locate the potential issue).

I use a standard set of dictionary files for each of my comps, and currently have stardict operating fine on 2 other laptops, both running 10.04, with the same set-up (xubu, same apps, and settings pretty much) and no indications of this problem on either (other) laptop.

I am no ubun troubleshooting guru, so if anyone has some advice it would be appreciated since I rely on stardict a lot while writing papers and doing research.

cheers,
tt

---

### Post by thaitang on 2010-12-31
ok well like I said stardict is a near crucial aid in my work and so I gotsta get it workin' right...welp I decided to purge everything to do with stardict including the dic files I have been using for the past 3 or 4 years with nothing but success.

I went and re-downloaded all of them again, plus a few others, and re-installed stardict from the repos. I added one dic at a time (/usr/share/stardict/dic/) for about the first 3 or 4 and checked to see if I could recreate the problem, which I could not and now it looks like everything is working tickity boo (fingers crossed, knocking on wood and rubbing my rabbit's foot that things work fine).

Sure makes me sit here saying "hrrmmm." I would be a lot more convinced that the problem is solved if  the same problem occurred on all laptops running after the upgrade, but that is not the case.

But it does seem rather odd that all of the files, except the repo packages for stardict have been the same and are currently working with two other laptops running 10.04 all loaded with the same deb files (I archive them during one install and use them on my other laptops b/c my internet connexion is deadly slow) and using the same dic files I have kept for a few years, that I just replaced as mentioned above.

Oh well I will definitely know the min it starts fuggering up again, if it does, but I hope what ever fixed it stays that way until the next LTS!

cheers,
tt

---

