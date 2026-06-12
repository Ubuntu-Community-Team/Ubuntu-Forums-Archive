---
title: "Unbuntu Server remote access"
date: 2006-05-10
forum: General Help
---

### Post by drpepper on 2006-05-10
Hi!

I want to make a server, that users can login into from the net, via a browser and they can access their their quota on the server. and when they login they aall see a common public area that can read/write aswell as their own private quota. i dnt want them to ftp into it, although i will setup a ftp for a public area but thats a different matter. I looked into setting a samba share that can be accessed via php page, but that doesnt seem very secure to me. it gotta be simple! and web based! any ideas anyone.

Thanks 

Nick

---

### Post by kb3hkg on 2006-05-10
Depends what you are looking for, it sounds like you want it to be for files in which case I'd recommend an scp/sftp solution, if it is just for access you might want just Openssh. I am not quite sure as to what you want your users to be able to do.

---

### Post by drpepper on 2006-05-11
sorry, for being unclear. I want the users to be able to log in via browser, and upload, download, delete, have complete control over their own area via the browser. i also want a public area, that the users have read/write permissions too. I want annoymous users to have read access to the public area via ftp. Thanks for ur reply

---

### Post by kb3hkg on 2006-05-11
A solution to this problem would be to use a backend like kerberos and give each user an account there and then use this for authentication and such through php. I do not know as to how easy that will be for you to setup though.

---

### Post by ZylGadis on 2006-05-11
Any modern browser supports the ftp protocol by typing [ftp://username:password@address/](ftp://username:password@address/) in the address box. So install an ftp server, configure it correctly, and you're done :)

---

### Post by drpepper on 2006-05-11
i think i cud get a kerberos authentication server going, but how do i tie it into my services? could u explain abit about the processes of users logging in via web, down to them accessing their resources. eg. php talks to apache web server --> kerberos ????

i dnt want the users just to ftp into their areas as ftp is not secure.

---

### Post by ZylGadis on 2006-05-11
Well, use secure ftp, then :)

---

### Post by kb3hkg on 2006-05-11
sftp or scp were my first suggestions. As for working with kerberos it would probably require some programs on the back end most likely perl or python to make the connection for authentication. I do not know how to do it exactly but do know it can be done and have seen it done.

---

