---
title: "admin problems"
date: 2010-02-05
forum: General Help
---

### Post by bigg6987 on 2010-02-05
I decided to upgrade my ps3 from 9.04 to 9.10. When the upgrade was complete, my wireless mouse would not work. I quickly formatted and returned back to 9.04. Ever since I've been back on 9.04, I've been getting messages saying that I didn't have authorization to do many different things, such as run the updates through the update manager. I've tried to add sudo users in the terminal, and I'm told that I don't have access to the sudoers folder. 

Please, anyone who may be able to help, feel free to offer any advice. I'm a fan of Ubuntu, and I've been considering trying YDL or fedora because of my problems. I've formatted my ps3 and reinstalled realistically 5 times already.

Thank you!

---

### Post by cariboo on 2010-02-06
If you are re-installing that many times, and you still can't do any admin tasks, you are either missing a step in the installation or not completing one properly. You problem is probably that your user isn't a member of the admin group. The simple way to check is to go to System->Administration->Users & Groups and check to seee if your user is a member of the admin group. If you aren't, I'm not familiar with a ps3 installation, but if you can start in recovery mode, drop to a root prompt and type:

```
gpasswd -a <user> admin
```

where <user> is your user name. Once you've added yourself to the admin group, type:

```
reboot
```

Once you are back at your desktop you should be able to run any admin functions.

---

### Post by Druke on 2010-02-24
Can you confirm whether you are in the "admin" group?

---

### Post by bigg6987 on 2010-02-24
I cannot get into a recovery mode, or a single user mode. The ps3 uses a program called kboot to boot into ubuntu, and I've been unable to find any documentation or directions as to how to get into recovery mode through kboot. I would have to say that I am not in the admin group, as I have no "change access".
 
appreciate the feedback

---

