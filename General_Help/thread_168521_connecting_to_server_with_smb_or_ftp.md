---
title: "connecting to server with smb or ftp"
date: 2006-04-30
forum: General Help
---

### Post by njzillest on 2006-04-30
I have just installed a network server to share files with my network.

I am able to connect to it when im on windows. (first i go to [http://landisk](http://landisk) - then i set the password) then i go to run and type "\\landisk"


i have a choice on the site for ftp or smb. WHat should i do in order to enter it with UBuntu? 

how can i acess the sserver. I tried to go to places-connect to server.

Im stuck there with a password. I dont know the password and i tried all the passwords that i had set earlier. 




thanks alot for the help

---

### Post by oliver123 on 2006-04-30
Not sure what's causing the problem... You should be able to go to [http://landisk](http://landisk) under Ubuntu and check (or set) the password. Then go to Places -> network -> windows network and see if the server is visible there.

If not, you should also be able to connect to it with that places -> connect to server dialog... Both ftp and smb should work... If it doesn't accept the username and password, does it give you an error message?

Also, if you installed a firewall in Ubuntu (by default there is no firewall, but you can install it manually), you should check that it doesn't block you...

Regards,
Oliver

---

