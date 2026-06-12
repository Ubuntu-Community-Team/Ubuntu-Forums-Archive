---
title: "Updated User Password Now Get &quot;Unlock Keyring Password&quot;"
date: 2011-02-26
forum: General Help
---

### Post by A4orce84 on 2011-02-26
Hello Everyone,

I am running Ubuntu 10.10, and I updated my password since I felt it wasn't something too secure. However, now when I start my system I continuously see "Unlock Keyring Password" and it is my old password.

Is there a way to update this to my new password, or update it to the behavior it was before....I never saw this message when I logged in previously.

Any help would be greatly appreciated.  Thanks.

--Asif

---

### Post by Dave_L on 2011-02-26
These are my notes for dealing with this.  They're for Ubuntu 10.04; I don't know if they're accurate for 10.10.

Open Applications >> Accessories >> Password and Encryption Keys, in the Passwords tab select "login", right-click on it, select Change Password, then enter previous and current Ubuntu user passwords.

Alternatively, if you've lost the previous password, delete the "login" keyring entry (right-click >> Delete), and add it as a new one (File >> New >> Stored Password), and name it "login". In this case, any stored passwords will be lost and have to be re-entered.

---

### Post by tredegar on 2011-02-26
Ubuntu's "gnome keyring" has been driving me mad too.

To reset everything my notes say "Delete all the files in ~/.gnome2/keyrings, logout, login, then start again".

When I am then prompted to re-enter passwords for the wretched "keyring" I leave everything blank, and click OK. "Save passwords insecurely?". Yes.

It then works.

My firewall is good, so should yours be.

Hope this helps.

---

