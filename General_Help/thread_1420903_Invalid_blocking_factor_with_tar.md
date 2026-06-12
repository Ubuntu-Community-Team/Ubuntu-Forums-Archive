---
title: "Invalid blocking factor with tar"
date: 2010-03-03
forum: General Help
---

### Post by Tom Atkins on 2010-03-03
I am trying to backup my system with a script I found here. It gives me an error message of invalid blocking factor for --exclude=lost+found I have no idea what this means. I tried to search this form for that message and received no hits.

Any help would be appreciated.

Tom Atkins

---

### Post by gmargo on 2010-03-03
This would be a lot easier if you posted the entire **tar(1)** command.  From the info you've given, I'd guess you have a "-b" or "--blocking-factor" option, with no argument or a null argument, just before the --exclude option.

---

### Post by Tom Atkins on 2010-03-04
Thanks for your message. The backup guide had tar cvpzfbackup.tgz at the start of the code. I just put a space between the cvpzf and backup.tarz and it ran fine. Your comment about -b made me try it. 

Thanks again

---

