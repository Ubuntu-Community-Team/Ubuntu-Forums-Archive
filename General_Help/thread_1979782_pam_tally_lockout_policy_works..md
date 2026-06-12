---
title: "pam_tally lockout policy works."
date: 2012-05-14
forum: General Help
---

### Post by dmobley88 on 2012-05-14
Hello everyone: I have found a very easy tutorial on how to enable a lockout policy in ubuntu. 
Note: DO NOT GIVE ME CREDIT for this tutorial. just surfing the web, and after an exhausting night of research, I found something that worked!!

So, here goes:

step 1: press CTL + ALT + T
            alternately, launch Terminal

Step 2: type  cd /etc/pam.d

step 3: type sudo nano common-auth

Step 4: enter your password

Step 5: add the following lines to the begining of the file [after the comment(s)] (do NOT include the - 's)
                   - auth required pam_tally.so onerr=fail deny=3
                   - auth [success=1 default=ignore] pam_unix.so nullok_secure
                   - auth requisite pam_deny.so
                   - auth required pam_permit.so

Step 6: press CTL + O
                          (this will write the file out)
that's it. 

This will lockout the account permenantly until the account is reset with the following command: sudo faillog -r

make sure you have another active account you can login to otherwise, you will NOT be able to reset your failed login attempts. I used my root account. I have tested this, and it works. There are no adverse affects on my system for enabling this. 

Enjoy. :)

---

