---
title: "Skype won't delete users"
date: 2010-12-28
forum: General Help
---

### Post by Total Noob on 2010-12-28
I allowed someone to access his Skype account on my computer (10.4). 

Now I can't delete his Skype name from the login process, which is set to autofill the first alphabetical user and seems to be unchangeable in that area. 

I tried deleting the software entirely, but that didn't do it. Somewhat bizarrely, the deleting the software itself did not delete any user data, and this raises security issues, ie, is the computer also holding other people's passwords?

Please let me know how I can remove this guy from autofill when I turn Skype on, and how to turn autofill off on the Linux version of Skype so I don't have to refuse the next person to borrow my computer.

Thanks.

---

### Post by Wtower on 2010-12-28
Take a look at:

[https://wiki.ubuntu.com/SkypeEthics](https://wiki.ubuntu.com/SkypeEthics)

You could try to completely remove Skype by running the following in terminal:

```
sudo apt-get purge skype
```

That may completely remove all relevant information as well.

---

### Post by gandaran on 2010-12-28
removing skype completely from the system doesn't remove the user data, to remove all the user data delete the /home/'user'/.Skype or just the /home/'user'/.Skype/ 'user_to remove' folder and restart skype again

---

### Post by Wtower on 2010-12-29
All right, good to know. Thanks gandaran

---

### Post by cathy duncan on 2010-12-29
Many thanks for this useful tip. I was also looking for the same command line.

---

