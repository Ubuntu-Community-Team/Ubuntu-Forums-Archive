---
title: "How to set up Samba to work with a folder that's outside server"
date: 2009-07-07
forum: General Help
---

### Post by oalexandrino on 2009-07-07
I'm trying to setup the samba server in the following way:

1) I have a server that will hold just the samba server, inside there we'll have just the user´s profiles file. everything about user's profile will be set there.

2) I have two other machines, but these are just desktop ones where I'd like to set up in the server (smb.conf) the user's rights to access some specifc folder in those machines. (those machine are windows xp ones)

this would be like so:

a) server machine

b) desktop machine I
- folderA
- folderB

c) desktop machine II
- folderA
- folderB

- user1 has access to folderA's desktop machine I
- user1 has access to folderB's desktop machine II
- user2 has access to folderB's desktop machine II
- user3 has access to folderB's desktop machine II

if a user try to access a windows share folder in a machine that has no permision. he/she wont be allowed.

remember, those folder are not in the Linux machines, they're in windows ones. but they must be protected by a samba server. that's it!

how to set up this?

---

### Post by Boondoklife on 2009-07-07
Let me see if I have this right, you want the shares on two windoes machines to be controlled by your ubuntu machine?

Only way that I could see this working would be to mount the windows shares on the samba server and then reshare this from the samba server.

Really this is a bad way to do things, is there a reason you need this type of setup?

---

### Post by oalexandrino on 2009-07-07
Yes, you've got what i mean.

I agree you. this is not a good way to do that.

Why do i need it?

it´s because i have a bad scenario to build a solution.

the machine that would hold the samba is being user by somebody who is not allowed to take a look at the files that will be controlled.

i know that i can make some configurations in order to give the appropriate permissions to files in the server to deny any access.

BUT by a politic scenario the files must be in another two windows machines.

in the next 20 days we'll receive a new machine to implement that in a better way. 

meanwhile i'd have implement it by using these resources.

if it is not possible, we'll have to implement manually by using windows xp permissions rights.

imagine many people, many resources and one very bad relathionship!

:(


> **Boondoklife said:**
> Let me see if I have this right, you want the shares on two windoes machines to be controlled by your ubuntu machine?

Only way that I could see this working would be to mount the windows shares on the samba server and then reshare this from the samba server.

Really this is a bad way to do things, is there a reason you need this type of setup?

---

### Post by Boondoklife on 2009-07-07
I personally think that the xp permissions would be a better solution and easier to implement, especially for a temp scenario.

---

### Post by oalexandrino on 2009-07-07
I see, but if I had to use a server to hold smb server and another server to hold the files to be managed.

how would i do that?

> **Boondoklife said:**
> I personally think that the xp permissions would be a better solution and easier to implement, especially for a temp scenario.

---

### Post by redmk2 on 2009-07-07
> ...if I had to use a server to hold smb server and another server to hold the files to be managed.

how would i do that?

A Samba server manages the files mounted on its _local_ filesystem.  Each host that serves file shares has a server component.  This includes Windows hosts that "share files" in an ad hoc environment (P2P).

---

### Post by Boondoklife on 2009-07-07
> **oalexandrino said:**
> I see, but if I had to use a server to hold smb server and another server to hold the files to be managed.

how would i do that?

As I said, you would have to setup the share on the windoes pc's then mount those shares onto the ubunti box and then share those mounts through ubuntu. You would be doing the same work as if you were doing the share from the windoes boxes and more.

If you want to do it that way then lookup how to mount samba shares and you will also need to read the samba tutorial. keep in mind this will require all 3 machines to be on to work correctly.

---

