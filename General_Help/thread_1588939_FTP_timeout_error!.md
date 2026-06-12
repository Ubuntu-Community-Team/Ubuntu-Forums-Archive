---
title: "FTP timeout error!"
date: 2010-10-05
forum: General Help
---

### Post by Alex1331 on 2010-10-05
Hi,

I've had this problem since I upgraded to 10.04.

If I connect to a FTP folder using Nautilus, it will not respond properly if a timeout have occured.
I sometimes have problems unmounting a FTP directory.

Do anyone know how to fix this?

For those who want to recreate the problem:
1. Connect to a FTP server.
2. Wait for some minutes.
3. Try to open another folder or file.

---

### Post by goltoof on 2010-10-06
.

---

### Post by goltoof on 2010-10-06
.

---

### Post by Alex1331 on 2010-10-06
This problem still exists in 10.10. :sad:

---

### Post by goltoof on 2010-10-07
For whatever reason my last posts won't show.

I have the same problem in Nautilus.  In terminal it times out for me all the time.  I realize it has to do with a setting on the remote ftp server.

My question is what setting do I need to change to keep ftp connections open longer?  I can't instructions on how to do that anywhere.

---

### Post by Alex1331 on 2010-10-10
Still no one who have a solution to this problem?:confused:

Ubuntu + FTP = FAIL :(

---

### Post by luvshines on 2010-10-10
Did you check the "idle_session_timeout" in vsftpd config file on the server ??
Default value is 5 minutes

---

### Post by Alex1331 on 2010-10-13
Timeout on the server is set to 5 min. I have this problem with all FTP servers, no matter if i use SFTP or FPT in nautilus.
Is it just my bad luck or what? :S

Another way to recreate the error:
1. Connect to a server using FTP/SFTP in nautilus.
2. Create a textfile and save some text in it.(gEdit)
3. Wait for a while and add some text.
4. Try saving...

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

---

