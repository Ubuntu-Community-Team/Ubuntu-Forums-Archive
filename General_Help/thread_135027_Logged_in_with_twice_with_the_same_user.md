---
title: "Logged in with twice with the same user?"
date: 2006-02-23
forum: General Help
---

### Post by Eric_T on 2006-02-23
I was trying to hibernate my computer, and wrote the following command:
$ echo -n mem > /sys/power/state

I realize now that I should've written "disk" instead of mem, but that's beside the point. After I did this command the computer shut down, and now when I've started it again, it seems like I'm already logged in. Firefox asked me to select another profile, and typing users in terminal yields my username twice.
So what I'm wondering is how do I log my "clone" off? I want my other Firefox-profile back, among other things!
Thanks:)

---

### Post by steve.horsley on 2006-02-23
Seeing your name twice in users is not a problem. There is one for your gnomse session, and one for your terminal window. Open another terminal and you will be there three times. Using who instead of users gives a little more info. You will see that all the different yous are on display :0 .

Not sure about firefox's problems though.

---

### Post by lamego on 2006-02-23
The abnormal shutdown did not allow firefox do delete it's lock file so now its reporting that another user "may be" using the profile.
If you rebooted your system you can be sure that you are not logged in twice, anyway you can check who the command "who" on a terminal.
To remove the mozilla lock file you will need to remove the lock file, from a teminal just type:
> rm .mozilla/firefox/*.default/lock

Firefox should open fine now...

---

### Post by Eric_T on 2006-02-23
Thanks, lamego, after running your command, then editing profiles.ini so that "default" became the default profile again, I'm back on track:)

---

