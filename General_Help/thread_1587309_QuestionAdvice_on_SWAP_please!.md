---
title: "Question/Advice on SWAP please!"
date: 2010-10-03
forum: General Help
---

### Post by listerdl on 2010-10-03
Hi I did the following command to see what swap space I have in terminal:

[COLOR="DarkSlateBlue"]**swapon -s**[/COLOR]

and the following results were:

Filename  Type         Size       Used    Priority
/dev/sda3 partition    2305316    0       -1

Can I just confirm 100% that the partition that I created, as per my screenshot, i.e. /dev/sda3 as a 2 GIG Swap partition as per the above information is being used?

I am sure the answer is yes I just want to be completely sure! THANKS!!
[IMG]http://www.simplytomoko.com/pictures/Screenshot.png[/IMG]

---

### Post by cj.surrusco on 2010-10-03
Yes, it is being used.

---

### Post by donato roque on 2010-10-04
If you go to your terminal and run top, you can confirm your swap size there and if it is indeed being used.

---

