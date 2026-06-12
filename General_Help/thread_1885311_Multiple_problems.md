---
title: "Multiple problems"
date: 2011-11-22
forum: General Help
---

### Post by ineeedyourhelp on 2011-11-22
first of all
when i accedently unplugged my laptop, the battery being no god, it shut down.
i reebooted and when my account tried to auto sign in iwas greeted with an error message about not being able to update some file and a log out button, looked for help but found none.
 then i got the bright idea to use the user account settings in the guest account to delete the original account i made.
then created a new account with the old user name but the new account did not ask for a pass word.
 the new user shows account disabled under password: thus my first want.
if i can activate this acount how would i?
every time i try to change an account password or sudo anything it gives me this

sudo: unable to change to sudoers gid: Operation not permitted

i think its because i am in the guest account
and now for my completely last resort how do i, if i can, restre ubuntu like a factory restore for a windows pc?

---

### Post by jerrrys on 2011-11-24
Ctrl Alt F6

will that get you to a usable terminal?

Ctrl Alt F7 will get you back to your desktop

---

### Post by boast on 2011-11-24
ahh, good 'ol ubuntu not having root account activated.

I think you'll have to use a liveCD in order to mount the partition and edit the sudo file to add the guest account.

---

