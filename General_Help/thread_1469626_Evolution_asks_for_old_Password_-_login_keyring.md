---
title: "Evolution asks for old Password - login keyring"
date: 2010-05-02
forum: General Help
---

### Post by BrokeMahPC on 2010-05-02
Hope this may help others - searching for a solution I found much of the info is out of date. 
I installed Lucid - my /home was on a separate partition so I did not format it to keep the original settings and mail.

When trying to send/receive mail, Evolution now asks for the old login password from the previous install to open the mail keyring.
"The password you use to login no longer matches that of your login keyring" There is a box to enter the old PW.

SOLUTION:
-Go to Applications-Accessories-Passwords and Encryption Keys
-Right click on **Passwords:**login
-Select Change Password
-Type your old login password in the "Old Password" field
-Type your new password in both the Password: and Confirm: fields.
-Click OK
-REBOOT

Evolution will now use your new login password to access the keyring.

---

### Post by haran_elessar on 2010-05-05
Thanks for posting this! I just installed Lucid and after installation decided to change the login password and every time I logged in I was prompted to enter the login keyring password since it was different than the login password; very, very annoying.

thanks to this I was able to change it. As you said most of the info for changing the keyring password is very old (at least the top Google results) maybe you should change the name of your thread to "resetting login keyring" so that more people can find it. It's very useful.

---

### Post by biofooled on 2010-05-05
The keyring password manager is called seahorse in case you want to run it from the command line (although the interface is GUI).  Also the reboot is unnecessary as far as I can tell.

---

