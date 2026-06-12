---
title: "I locked myself out of my box!"
date: 2011-07-25
forum: General Help
---

### Post by stevennlv on 2011-07-25
I locked myself out of my box.
 
I just (finally) got an install on my box.
 
I was doing some house keeping and changed my default password to a more secure one.
 
I have it written down.
 
I ***_KNOW_*** I'm putting it in correctly.
 
Authentication fails.
 
How do I fix it?
 
All help greaaatly appreciated.
 
Thanks.

---

### Post by nothingspecial on 2011-07-25
Try capslock and that sort of thing. If all else fails, restart and choose recovery mode at the menu where you would choose between windows or linux

Choose root shell in the next menu.

Type
```

passwd steven
```

change steven for your actual username.

Change your password and repeat it when prompted. (you will see no indication that you are typing anything.

Type ```
exit
```

Then resume aq normal boot.

---

### Post by stevennlv on 2011-07-25
Thankx,

You saved my bacon.

I was digging through the book and it didn't really get in to how to use the passwd command in root.

Thanks for clearing it up.

But, this created another problem, time for a new thread.

---

