---
title: "Can' t read SD Card"
date: 2012-08-01
forum: General Help
---

### Post by joelstitch on 2012-08-01
I have a sd card that I formated to root a Nook Tablet and now its not showing up on Ubuntu, Windows XP or Mac. I would like to format it but I can' t if is not readable. What can I do?

---

### Post by audiomick on 2012-08-01
What did you format it with? Whatever your did that with should still be able to see the card. 

What was the card formatted to? Is it perhaps a format that is not visible to the tools you have used?

---

### Post by sgoodman on 2012-08-01
[LIST=1]
[*] Find the device the card is registered, enter ls /dev/sd* before and after plugging in the card.
[*]you will find a device like /dev/sdb
[*]now you can mkfs.ext4 or whatever you like the card
[/LIST]

---

