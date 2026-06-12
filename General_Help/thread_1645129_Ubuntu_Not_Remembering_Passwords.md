---
title: "Ubuntu Not Remembering Passwords"
date: 2010-12-14
forum: General Help
---

### Post by ep1centre on 2010-12-14
Hello, 

I'm fed up of trying to get Ubuntu to remember passwords, its a nightmare having to enter passwords every time you want to do something....

OK so maybe not Ubuntu itself but some of its components, on my neighbours installation (which I manage) it insists on asking him for his e-mail password every time the computer is restarted (Evolution client) now why does it do that on his computer yet none of mine ask me for the e-mail password and I too use Evolution?

On mine the thing that really hacks me off is every time I want to access a shared network drive it asks me for the password for that particular share, lately its got even worse when I mapped an SFTP share which I need access to for work and it not only asks for the password (which is as complicated as you like) it also asks for a user name which is equally as bad, now tell me what's the point of clicking "remember forever" when the next time i start the computer I'm back to square one and i have to enter passwords all over the place to access anything?

Hope somebody can shed some light on the situation.

Thank you.

---

### Post by flagstar on 2010-12-14
I'm not sure about your problem but from what I know, it was essential for Ubuntu to prompt for password to protect its content from being access by anonymous. And that's some of the reason why Ubuntu doesn't need any anti-virus to protect it's system. It was a pain at first but sooner or later you'll get used to it.

"Remember Forever" option is pretty much not recommended to be used even if you want quick access to Ubuntu like Windows did but it wouldn't work anyway if you try it.

---

### Post by tredegar on 2010-12-14
I don't use evolution, so I can't help you with that.

The solution to your SFTP asking for passwords is easy: Just set up ssh to use private / public key based authentication. Instructions are [here]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch17_:_Secure_Remote_Logins_and_File_Copying") (scroll down to "Using SSH and SCP without a password".

Now, in my "Places" menu I have tred@laptop tred@server etc. One click and I'm there. No password or anything else is required.

---

### Post by ep1centre on 2010-12-14
> **flagstar said:**
> I'm not sure about your problem but from what I know, it was essential for Ubuntu to prompt for password to protect its content from being access by anonymous. And that's some of the reason why Ubuntu doesn't need any anti-virus to protect it's system. It was a pain at first but sooner or later you'll get used to it.

"Remember Forever" option is pretty much not recommended to be used even if you want quick access to Ubuntu like Windows did but it wouldn't work anyway if you try it.

No offence there but if an option is there, wether its recomended or not, it should work, hacks me off clicking something that says "remember forever" only to find it's gonna ask me the same thing over and over after each time the system has been powered down.

But i have no problem with Ubuntu asking me for the root password for "sudo" commands or system updates or software installation, that's not a problem at all what i can't stand is after sticking my password in to log into the computer i have about 6 network drives mapped that i need access to to do my work and each one is password protected with a different password.

Lately the one that i've just lost it with is when we've started colaborating with people off site and as such we set up an SFTP or SSH (whatever its called) drive which is being hosted by 1&1 so setting it up was pretty easy just click here and there, what i dont get is why every bloddy time i click the "mapped" drives after logging in i have to stick my password in and like i said lately the SFTP thing asks for both user name and password - that's what i'm annoyed about i keep clicking "remember forever" and then it just doesnt.




> **tredegar said:**
> I don't use evolution, so I can't help you with that.

The solution to your SFTP asking for passwords is easy: Just set up ssh to use private / public key based authentication. Instructions are [here]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch17_:_Secure_Remote_Logins_and_File_Copying") (scroll down to "Using SSH and SCP without a password".

Now, in my "Places" menu I have tred@laptop tred@server etc. One click and I'm there. No password or anything else is required.



Thanks for the link, i read the section you mentioned but it went a little over my head - as i mentioned above the FTP Folder is hosted by a third party hosting company I wouldn't have a clue where to start looking for said file to alter, i don't get why I'd have to alter anything on the remote computer anyway, all I'd like is for ubuntu to remember my passwords for all these drives and send them when i click on a mapped drive in "Places" - much like firefox does with website logins, the ability for the OS to do it seems to be there otherwise it wouldn't ask if I want it to remember the passwords but it just doesn't seem to work properly.

---

### Post by QLee on 2010-12-14
It can be difficult to explain things clearly to someone who is severely, "hacked off".

Are you sure it's Ubuntu requiring you to authenticate on those mapped network drives or might the request be from the systems they are on?

I once saw a laptop running an insecure Operating System which, when the user inadvertently let a rootkit install, allowed the malware access to his employer's network.

As far as your neighbour's Evolution, have they or you checked the preferences for the account? However, if it is a laptop, I don't recommend checking remember password, if it is lost, whoever finds it, or who took it, becomes that user for the email account which can cause many headaches for the original user.

---

### Post by tredegar on 2010-12-14
> Thanks for the link, i read the section you mentioned but it went a little over my head
Well, I asked you to scroll down because much of the earlier stuff is to do with *installing* **ssh** (which you have already done). But you could perhaps find the time to read the link from start to finish, because there is a good explanation of how it all works together.

I am pretty sure 1&1 offer linux servers, you might try asking them for help setting up **ssh** on the server you are paying for, and they are hosting.

> i don't get why I'd have to alter anything on the remote computer anyway

You don't really have to "alter anything on the remote computer", you just need to give it your _public_ **ssh** key. 

1&1 will have met this problem many times before and I expect they will be able to help you if you ask for help to set up "Public / Private key authentication for sftp".

If you have more than one PC on your network, may I suggest you try setting this up on your LAN before you try to use 3rd parties (1&1)? This will familiarise you with the steps you need to take, and you can probably experiment in the comfort of your own home.

For example, my "Places" menu has tred@server and this resolves to **sftp://tred@server/home/tred** and it "just works".

Try this on your LAN and then when when 1&1 ask you for your "DSA/RSA Public key", you'll know just exactly what they are asking for, and will not make mistakes.

> Lately the one that i've just lost it with is when we've started colaborating with people off site and as such we set up an SFTP or SSH (whatever its called) drive which is being hosted by 1&1 so setting it up was pretty easy just click here and there

The bottom line is this: Linux has *always* taken security very seriously. This means you cannot usually "just click here and there"  and connect. _You_ have to set the permissions and security checks up yourself, and it is *assumed* that if you are going to do this yourself, you will have read the documentation, understood it and therefore  know what you are doing. 

It is (perhaps purposely?) built so that if you do not know what you are doing, and do everything just _exactly_ right, it will not work.

But think about it: What use is an OS that lets you configure what you _believe_ to be a "secure connection", when it's not? The upside is that if it works, and connects with **ssh** then it's probably secure. If it doesn't then you have perhaps misunderstood something very important.

I like this approach.

@QLee
Your points are spot-on. Thank you & I hope the OP considers them.

---

### Post by ep1centre on 2010-12-16
Thanks for the kind words there, i was having a bit of a bad day the otherday.

I'm assuming when you say experiment on your network you mean  set up a load of things in terminal?

I swear i'm trying my best to learn ubuntu, but it's proving to be one hell of a task, i still get frustrated trying to do anything sometimes even simple and you need to turn to a command line and type up a load of stuff with to be honest i dont understand to get things working.

Anyway besides the point, from reading you post it leads me to beleive that you're trying to help me "set it up", however i have set ecerytjing up to a degree that it all works as it should, exept for it asking me for a password for the remote location whichever it might be everytime the computer shuts down and restarts again - no offence intended here as you obviously know what you're doing as you have your system working as you want it :) but how does public/private keys on the remote host help me as problem seems to be that my local machine running ubuntu wont save any passwords to then transmit them when prompted by the remote system.


@ QLee

Where the request comes from in my eyes (i can be wrong) is besides the point, the problem is to (me anyway) being asked for the same password everytime i wanna access one of my networked drives, why doesnt the system just remember what i type in, and before someone goes down the safety and secure line stop and think, if the people who wrote ubuntu thought intended for it not to remember passwords then why does it (along with user name/password combo) ask me to chose to never remember, only remember during this session OR >>>Remember Forever<<< only to ask for the password again next time i start up the computer.


About the Evolution email client, its not on a laptop its on a desktop so no problems there and yes i've checked the setting and the box that says something along the lines of "remember authentication password" is ticked and once again that sistem seems to like asking for the password everytime the email client is started.

---

