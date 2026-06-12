---
title: "Help with Samba configuration"
date: 2011-01-13
forum: General Help
---

### Post by rededit on 2011-01-13
I was wondering if I could get some help with a Samba issue. I installed samba file server and configured it to share the users home directory. I have two users that will represent groups of people at work. Users are xemployee and xmanagement. Windows I guess will only let you connect with one set of credentials at a time. In my case I cannot connect to the management share using the credentials for management and then go into the employee share using the employee credentials. If I try I get this error:

Multiple connections to a server or shared resource by the same user, using more then one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again. 

From what I read this is a Windows issue. I was able to verify this using net use to drop my connection, but I want the server to transparent. I do not want management in this case to deal with the issue. There is a work around that I learned of from [here]("http://support.microsoft.com/kb/938120") but this still is something that management will have to deal with when they need access to both. It also mentions that I can create a domain alias, which I am not totally sure what that is. I have already created a local domain x.local and that works with my browser to point me to the webserver but it does not work like: \\x.local\xmanagement to access the share.  It will allow me to use \\192.xxx.x.xxx\xmanagemnet, but once again I want the server to be transparent and I don't want to go to every computer and map a share location. I want management to be able to go to network and see the shares they need and be able to access them. So I guess what I am shooting for is to give management access rights to both xmanagement and xemployee , and the employee to only have access to the xemployee share. I am wondering if I can just configure this with samba alone for now. I read a little about configuring samba with a domain, but I am kinda confused about that too. I have had jobs where I log into a domain that is run on a windows server to get like roaming desktops for example. Is this the same type of domain that I set up as x.local? I would like to implement something similar at my workplace down the road so if anyone has some links or info on that I would appreciate it as well. My immediate issue though is to give xmanagement access rights to xemployee as well as it's home samba share. One last piece of info, I used 
[B]sudo chmod 0750 /home/xmanagement and 
[/B][B]sudo chmod 0750 /home/xemployee to block on group from seeing the other,
then I went ahead and changed xemployee back to 0777 hoping that would fix
my issue but it did not. 

And with samba shares is there a connection limit as in how many people can 
connect to a share? 

Sorry for the long post I just wanted to present all the details to someone
who might be willing to help.

Thanks in advance!
[/B]

---

