---
title: "Keeping drivers up-to-date"
date: 2012-05-19
forum: General Help
---

### Post by samwillc on 2012-05-19
Hi everyone,

I used a driver from the following source to get my printer up and running:

[https://launchpad.net/~baltix/+archive/ppa/+build/3302389]("https://launchpad.net/%7Ebaltix/+archive/ppa/+build/3302389")

(USED THIS ONE) BUILT FILES: [cnijfilter-mg6100series_3.60.2-0~15~natty1_amd64.deb]("https://launchpad.net/%7Ebaltix/+archive/ppa/+build/3302389/+files/cnijfilter-mg6100series_3.60.2-0%7E15%7Enatty1_amd64.deb")         (1.8 MiB)

How do I keep the drivers updated or keep a check when new ones are out?

Do I add a PPA to software sources and it uses that URL to update the drivers? Not really sure how it works in ubuntu 12.04. For example, I have seen:

"Add webupd8's PPA to your sources.list" on a webpage which led me to the conclusion above.

Obviously it's different from clicking on 'windows update' so I'm a bit lost. Any clarification would be very helpful indeed.

**plus - how do I know what sources are on this list?**

Thanks,

Sam.

---

### Post by Cheesemill on 2012-05-19
To add the PPA to your system type the following into a terminal:
```
sudo add-apt-repository ppa:baltix/ppa
```
Your driver will now be kept automatically updated.

---

### Post by 3rdalbum on 2012-05-19
> **Cheesemill said:**
> To add the PPA to your system type the following into a terminal:
```
sudo add-apt-repository ppa:baltix/ppa
```
Your driver will now be kept automatically updated.

Not quite, you need to update your package list after adding the PPA:

```
sudo apt-get update
```

Run that after doing the sudo add-apt-repository command Cheesemill mentioned.

---

### Post by Cheesemill on 2012-05-19
> **3rdalbum said:**
> Not quite, you need to update your package list after adding the PPA:

```
sudo apt-get update
```Run that after doing the sudo add-apt-repository command Cheesemill mentioned.

I didn't mention this because no packages were being immediately installed from the PPA, the 'apt-get update' would happen automatically the next time the system checks for updates :)

---

### Post by samwillc on 2012-05-19
Thanks for the replies.

It's very helpful :D

Sam.

---

### Post by samwillc on 2012-05-19
Sorry, one more.

[cnijfilter-mg6100series_3.60.2-0~15~natty1_amd64.deb]("https://launchpad.net/%7Ebaltix/+archive/ppa/+build/3302389/+files/cnijfilter-mg6100series_3.60.2-0%7E15%7Enatty1_amd64.deb")         (1.8 MiB)

I ran the above file again on a new fresh install and the software centre opened up saying 'upgrade available'.

Does this now mean that the PPA has been added to the source list or do I have to still add it via terminal like in your instructions?

Thanks.

Sam.

---

