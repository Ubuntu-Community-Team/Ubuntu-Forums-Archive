---
title: "Import outlook from xp"
date: 2010-03-26
forum: General Help
---

### Post by panti19 on 2010-03-26
i want to install ubuntu on a computer which now has windows xp. I want to use the entire disk. I only want to keep email information (user/password) from Outlook. can i do that?

thanks

---

### Post by oldfred on 2010-03-27
If you are not dual booting, you may want to convert to thunderbird in XP and then backup your entire thunderbird profile. I share one profile and dual boot XP and Ubuntu and use the same profile. I have not converted yet to the new version, so I am not sure about what changes that will entail.
[http://kb.mozillazine.org/Import_.pst_files](http://kb.mozillazine.org/Import_.pst_files)

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
More info:
    *  (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (SeaMonkey) ./seamonkey -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by panti19 on 2010-03-27
thanks but will this work if i don't know the password any more?

---

### Post by panti19 on 2010-03-27
bump

---

### Post by underquark on 2010-03-27
So, are you really asking how to find out the password for Outlook on a Windows XP system?

---

### Post by panti19 on 2010-03-27
no. i don't want to find out the password. i just want to use the email account I use on a windows machine which works reaaaaally slow.I want to install ubuntu on that machine and use the account. but i don't know the password anymore..

---

### Post by krismatth3 on 2010-03-27
No, you will need to know the password. It also depends on what type of connection outlook is using - go to Tools->Accounts. Is it an exchange server, imap, pop3? 

You will not be able to install ubuntu over windows, and keep the outlook data. You'll have to back it up first, and then restore it inside ubuntu.

---

