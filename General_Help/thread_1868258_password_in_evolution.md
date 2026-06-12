---
title: "password in evolution"
date: 2011-10-24
forum: General Help
---

### Post by iacoposk8 on 2011-10-24
Hello everyone! I have a couple of problems with evolution:
 1) as soon as I open it always asks me the password (even though I told him to memorize it)
 2) and then always show me this message: "Enter password to unlock your login keyring
The password you use to log in to your computer no longer matches that of your login keyring. "

how to fix this?

---

### Post by bantuvez on 2011-10-24
This may solve your second problem and perhaps also the first:   

Open up Seahorse: Go to System->Preferences->Passwords or alternatively type "seahorse" in terminal. If you want your keyring to be opened when you login, your passwords should be under the "login" keyring. If you see more keyrings in Seahorse (e.g. you have a "login" keyring, and another named "default") then you have to delete the other keyrings, and leave only the "login" keyring. Then reboot. This way you will only have one keyring which will open up when you login. (Note that if you use autologin this won't work.) Note that Ubuntu will forget the passwords you stored in the deleted keyrings, so you will have to retype them one more time when ubuntu asks for them, to store them in the "login" keyring. In Seahorse you can see which password belongs to which keyring.

---

### Post by iacoposk8 on 2011-10-24
Thanks for response, and then I feel tonight I tell you:)
 thanks:)

---

### Post by iacoposk8 on 2011-10-24
Unfortunately I only see the password in the login keychain :(
 in the other two cards there is nothing, it's all empty.
 can that be?

---

### Post by bantuvez on 2011-10-24
You should delete the empty keyrings. (Right-click -> delete)

---

### Post by iacoposk8 on 2011-10-24
So it must be empty? There should be no door keys?
 Even I have to delete the log?

---

### Post by bantuvez on 2011-10-24
So, just to be clear:

In Seahorse, on the first tab (Passwords) you can see your stored passwords organized into keyrings ("folders"). If I understand, you see here 3 keyrings, but only the the keyring named "login" stores any passwords. If this is the case, the other two empty keyrings ("folders") can be deleted.

I don't know what is a "door key". You don't have to delete any logs.

---

### Post by iacoposk8 on 2011-10-24
forgive my English: D
 with "door key" I mean "keyrings"
 in the first tab (password) I have only: password: login
 I delete it? (it is just that, no more)

---

### Post by bantuvez on 2011-10-24
Okay, then don't delete it. 

Can you see your e-mail password in the list of the stored passwords?

You can try changing the password of your login keyring (right-click -> change password). Change it to your login password. Maybe this can help.

---

### Post by iacoposk8 on 2011-10-24
I see this:

[IMG]http://i675.photobucket.com/albums/vv120/iacoposk8/Schermatadel2011-10-24203108.png[/IMG]


   the interesting thing, I forgot to say is that I can never to enter the correct password in that window.
 this makes me think ...
 in my computer there are two accounts, mine and a super-users.
 may be that it refers to the password of the super users?

---

### Post by bantuvez on 2011-10-24
Okay, that's problem. You have to reset the password of the login keyring to your login password. I don't think that the other user account is the cause of the problem. I think Seahorse doesn't list keyrings of other users. 

Maybe you can try deleting your login keyring (if ubuntu allows you to do so), I think in that case Ubuntu will make a new login keyring for you. But I never tried this.

Alternatively you can set up a new keyring in seahorse:  File->New->Password_keyring, give it a name, and a password. Then make it your default keyring: right-click on the just created keyring, and click "Set as default". So from now on your applications (e.g. Evolution) will store there password in this keyring. The problem with this is that after logging in you will always have to type the password of the keyring, to open it up. Maybe you could try giving you login password as password of the keyring, but I think it still won't open automatically after you log in.

---

### Post by iacoposk8 on 2011-10-25
I did! it's like you said!
 Now he asks me the password and then just start evolution.
 It's not perfect but it is already a solution that is really quite nice, thank you:)

---

