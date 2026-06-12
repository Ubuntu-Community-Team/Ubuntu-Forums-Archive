---
title: "Grub Error..."
date: 2010-01-04
forum: General Help
---

### Post by Dodger101 on 2010-01-04
I turned my laptop on this afternoon to receive the following screen...:

     ```
GRUB loading.
error: the symbol 'gbuB_st2len' not found
error: unknown command 'terminal'
error: the symbol 'gbuB_st2len' not found

 Failed to boot default entries.

Press any key to continue... 
I can get nowhere from this screen...
```A quick google search returns 0 results for the grub error [IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/confused.gif[/IMG]

The laptop is running xubuntu 9.10, and is been recently updated. I don't know what version of grub it's running, but should be up to date.
If there's any other information you would like (and I would know off the top of my head!) then please ask...

Thanks very much for any help.

...Dodger

---

### Post by Leppie on 2010-01-04
well, this isn't a grub message...
looks like someone is fooling around...
"grub stolen"??? since when do people "steal" grub?

---

### Post by Dodger101 on 2010-01-04
I think that the proper error message should be grub_strlen, not gruB_st2len.... :(

If the error message isn't even printing correctly then something must be corrupt right? :(

---

### Post by Leppie on 2010-01-04
well, you could try re-installing grub2. I suppose you did a clean install?
could you post the output of this command:
```
$sudo blkid
```

---

### Post by Dodger101 on 2010-01-04
..Sorry, I can't post the output of any command or reinstall at the moment as I can't boot past that error message, I would have to use a live cd and chroot into the environment...

I may try doing that tomorrow, but I wanted to know if this was a grub problem or something deeper... I'm worried my hard drive may be busted.

---

