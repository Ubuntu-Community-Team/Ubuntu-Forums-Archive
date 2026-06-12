---
title: "Finding apps after a fresh install"
date: 2009-10-29
forum: General Help
---

### Post by Bou on 2009-10-29
Hi,

I was introducing Ubuntu to a coworker today, after a lot of complaining about viruses on her part and a few hints on mine. I used a live CD on one of our computers, and guided her through the basics. She was very impressed and eager to further try it when she got home.

There was one thing, though. When I was telling her how easy it was to install software, I opened the software center and searched the word "amule". Instead of showing me the app and giving me the option to install it, the software center told me there were no candidates or something of sorts.

So, I take it after a fresh install you have to refresh your repository info before actually searching for any program. But the software center does not let you do that and software sources does not seem to give you any obvious way either. I want to give my workmate an uncomplicated way to do it on her own, but... is there one at all?

---

### Post by philinux on 2009-10-29
You need to open system>admin>software sources and tick the first 4 under ubuntu software, and tick the partner repo under third party software.

Then of course you will need to do the RestrictedFormats and Medibuntu dance. Links below. Seems a faff but its the **legal stuff**.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Maybe you need to explain that this is a one off exercise.

---

### Post by fooman on 2009-10-29
i believe amule is in the universe repos,  which will need to be enabled in software sources....and yeah,  it is fairly uncomplicated:

go to system > administration > software sources

under the "ubuntu software" tab...put a chcek next to the first 4 choices (main - universe - resrticted - multiverse),  then click "close"

you will see a warning that the repos are out of date and need to be reloaded.  click the "reload" button and when it completes,  you should be able to find amule in the software center.

hope that helps.

---

### Post by Bou on 2009-10-29
Thanks guys, that's what I thought she would have to do. I still think it can be confusing for a total newbie, but what can you do...

---

### Post by celtic426 on 2009-10-29
> **Bou said:**
> Thanks guys, that's what I thought she would have to do. I still think it can be confusing for a total newbie, but what can you do...

Another easy way is the website: [http://getdeb.net]("http://getdeb.net")

Has a lot of popular software with easy to download .deb files, which should be pretty easy for a newcomer.

---

### Post by DougieFresh4U on 2009-10-29
Also, when **Ubuntu software Center** is open, go to **View** and make sure **'All Applications'** is selected.

---

### Post by ingeon on 2009-11-07
> **celtic426 said:**
> Another easy way is the website: [http://getdeb.net]("http://getdeb.net")

Has a lot of popular software with easy to download .deb files, which should be pretty easy for a newcomer.

Is there a way i can just add the entire getdeb to my software repo in intrepid/jaunty/whatever and how?

I am looking for a repo similar to Suse`s packman (3rd party heaven) but for ubuntu.

---

