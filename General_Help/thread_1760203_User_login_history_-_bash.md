---
title: "User login history - bash"
date: 2011-05-16
forum: General Help
---

### Post by garcy on 2011-05-16
Hello everyone,

I need to make a bash program that will print the number of times and how much time users have been logged in during a certain time period(two dates given by command line agruments - ./login.sh 27/04 06/05).

The result must look something like this:

username | no. of times this user has been loged in | how much time this user has been logged in(days hours:minutes)

example:

johnk 2x 0 days 2:46
deanb 4x 0 days 11:42
lukas 2x 0 days 1:58
peterp 3x 1 days 18:41

Any help would be appreciated. Thank you

---

### Post by r-senior on 2011-05-16
Have a look at the "last" command. There is a limit to how far this goes back, depending on how the system is configured, but I assume this is a shell scripting exercise?

---

### Post by nothingspecial on 2011-05-16
Is this homework ????

If not, why do you need to know this?

Hi, by the way:D

---

### Post by garcy on 2011-05-16
> **r-senior said:**
> Have a look at the "last" command. There is a limit to how far this goes back, depending on how the system is configured, but I assume this is a shell scripting exercise?

Hi,

thank you for your quick answer. I have already used the last command.  However I don't know how to convert the information returned by this  command into the following form:

johnk 2x 0 days 2:46
deanb 4x 0 days 11:42
lukas 2x 0 days 1:58
peterp 3x 1 days 18:41

I would like to know how to get the number of users, their user names,  how many times this user has logged in and how much time they have been  logged in.

---

