---
title: "Headless server won't let me execute an exe  (vs a desktop where it works)"
date: 2011-01-22
forum: General Help
---

### Post by Valmond on 2011-01-22
Hi all!

I have now had an Ubuntu desktop server on a very crappy server (network filesystem with enourmus latency) for a year
and as the subscription will soon run out I opted for a slightly better one, still crappy but at least a "complete server" (cpu+mem+HD).

And a headless installation of Ubuntu Server 10.10 "Maverick Meerkat" instead of my Desktop version.

I'm not using it for web pages or other 'ordinary' things though, I'm running my
homemade MMORPG off of it and this new headless situation is a bit unclear to me.

I created an account and password with my root account, a folder with the username
was created in /home/ and I uploaded my mmorpg executable there with an ftp client.

A quick
chmod 777 Server
and I tried to launch it:
./Server

Ubuntu answers:
.Server: command not found

I tried to change the whole folder (being root) to 777 but it didn't work either.


What have I missed?

---

### Post by dcottingham on 2011-01-22
I'm concerned about this part:
> Ubuntu answers:
.Server: command not found
It shouldn't have said ".Server", it should've said "Server". So I'm thinking you might have mistyped "./.Server" where you meant "./Server". Can you check?

---

### Post by Valmond on 2011-01-22
Firstly thanks for reading and trying to help.

To check if I did something wrongly I reconnected with my 'new' account and tried:

./Server

answer:

-bash: ./Server: No such file or directory


a simple 'ls' gives me this: (normal, I uploaded this with FileZilla)

config.xml Data Lua Map Server


I disconnected and relaunched putty, connected with root and did the same thing and got exactly the same answer.



So maybe I copied thing erroneously or maybe disconnecting / reconnecting made something (I am at lost here) but I'm quite sure it said ".Server" and not "Server" or "./Server" or "-bash something..."
Well, hopefully someone knows what's going on or can point me in the right direction.

Of course I'll investigate further but any kind of enlightenment will be greatly appreciated.

---

### Post by dcottingham on 2011-01-22
I suspect it would be illuminating if you tried "ls -l" and posted the result.

---

### Post by tcrapper on 2011-01-22
Try changing the permissions to 755 instead of 777.

---

### Post by dcstar on 2011-01-23
If you are trying to "execute an exe" then you need Wine installed.

You also need to specifically run it with the wine prefix as only Desktops associate file types.

---

### Post by Valmond on 2011-01-23
@dcstar

That's it!

So you can't do that... or is there a way around? (I'm off checking our friend google :) )

---

### Post by Valmond on 2011-01-23
Thanks, solved!

---

