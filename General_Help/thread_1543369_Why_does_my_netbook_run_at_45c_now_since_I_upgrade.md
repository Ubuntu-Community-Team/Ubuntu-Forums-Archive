---
title: "Why does my netbook run at 45c now since I upgraded to 10.4?"
date: 2010-08-01
forum: General Help
---

### Post by hedgeborn on 2010-08-01
Any ideas?

It's a Dell Lattitude 2100. Ran cool as a cucumber under 8.04.

Ever since I upgraded to Lucid Lynx this thing gets noticeably warm on the bottom for the first time ever and regularly runs at 45c under low load. There are no crazy processes running. Only difference between now and before is I was running the LPIA Dellbuntu 8.04 and was formatted ext3. Machine now is running Ubuntu 10.4 netbook and formatted ext4.

I miss my nice cool netbook. What's the deal? :(

---

### Post by giddyup306 on 2010-08-01
> **hedgeborn said:**
> Any ideas?

It's a Dell Lattitude 2100. Ran cool as a cucumber under 8.04.

Ever since I upgraded to Lucid Lynx this thing gets noticeably warm on the bottom for the first time ever and regularly runs at 45c under low load. There are no crazy processes running. Only difference between now and before is I was running the LPIA Dellbuntu 8.04 and was formatted ext3. Machine now is running Ubuntu 10.4 netbook and formatted ext4.

I miss my nice cool netbook. What's the deal? :(
I'm not 100% sure, but it seems that after I upgraded to Lucid that my CPU was taxed a lot more than with any other version going back to 8.10.  

I'm curious myself...

---

### Post by hedgeborn on 2010-08-02
My CPU doesn't seem to be working any harder than before, there is a definite difference in temperature though.

I really wish there was more being done to improve Ubuntu's performance on laptops as far as battery life and temperature etc. All you have to do is google Ubuntu or Linux + laptop temperature and you quickly find its been an ongoing problem.

It's frustrating to hear that people run Windows 7 :roll: and enjoy a nice long battery life and a cool running machine while laptops still seem to be an afterthought for our community.

I don't want to run Windows. I just want my OS of choice to have the right pieces in place to manage temperatures on a laptop or netbook.

---

### Post by utnubuuser on 2010-08-02
45C is reasonably cool.  My thinkpad hovers around 47-52C and up to 70C with a flash-intensive site running.

There are several how-tos floating around about disabling un-needed services etc, thereby improving battery life and reducing cpu load.

I'd be inclined to read up on kernel optimization to really get a handle on having slim and trim OS.

for laptops there is also a little app called powertop which will run through the system and make suggestions on how to improve performance

I've noticed too, that with the new LTS, there are several processes and apps that are continuously and periodically writing to disk. that's probably not necessary and can be switched off.

Almost guaranteed that most of the heat and powerconsumption is from hdd usage.

---

