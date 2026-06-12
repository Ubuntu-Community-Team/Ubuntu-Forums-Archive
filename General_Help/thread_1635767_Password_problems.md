---
title: "Password problems"
date: 2010-12-02
forum: General Help
---

### Post by bvbellomo on 2010-12-02
I bought a netbook on e-bay with Ubuntu (9.10 I think).  Unfortunately, the seller never told me the root password, and I don't have a CD drive, floppy or any other way I can find to reformat.

I think the password for the default user might be blank.  Is there a way to test this?  It automatically logs in when I boot, and it behaves differently with a blank password from a wrong password, but it doesn't seem to accept sudo commands.

Is there a way to reset the root password without knowing it?  The account I log in as has privileges to almost everything.  Is there a way to reset the root password without a full reformat, assuming I can get access to the drive?

---

### Post by nothingspecial on 2010-12-02
There is no root password in Ubuntu.

To make a new one for yourself, see this

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by wojox on 2010-12-02
Sure [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword")

---

### Post by HermanAB on 2010-12-02
I would re-install.  That is the only way to be sure that you have a good system.

---

### Post by bvbellomo on 2010-12-02
To clarify, I would reinstall if I were able.  I can't figure out how to boot from anything other than the solid state disk that is soldered onto the main board.

---

### Post by k50aker on 2010-12-02
> **bvbellomo said:**
> To clarify, I would reinstall if I were able.  I can't figure out how to boot from anything other than the solid state disk that is soldered onto the main board.
You should be able to access the filesystem via single user mode in the grub menu. there you can just go to the /etc/shadow file and delete the password. the password for root should be on the first line of the file and should be a long string of letters and numbers and should look something like this:

root:$6$MD8Qc6QI$kwLC7zkUhIVl5cFyycvD7GpLkHT7q6.XYw3eOvufA8S35pxgW87WP5/ACwwxOx6wRMebwWjN7SCTQfMbQXHR71:14909:0:99999:7:::

You should only delete the entry from the first colon to the second one, otherwise you would screw up the system completely.

You can use the vi editor to edit the file in command line.

hope this works for you.

---

