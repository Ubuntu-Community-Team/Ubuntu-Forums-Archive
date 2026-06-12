---
title: "Creating the less passwordish experience on Ubuntu"
date: 2011-03-28
forum: General Help
---

### Post by ursoouindio on 2011-03-28
Hey folks

My mom have been complaining a lot lately about her laptop, mostly because she didn't know what to do with Windows, Flash, Java, Anti-Virus,...  asking for updates, sometimes even in English (and she can only understand Portuguese). She cant manage this kind of things, her knowledge on computers is just extremely basic. She just wants to turn her laptop on and exchange emails with her friends.

So I decided (and convinced her) to put Ubuntu on her laptop. I actually just did it and now I'm trying to make it the easiest as possible for her to not get upset by this experience.

One thing that I would like to make is a "passwordless" use. She should be able to turn on her laptop, log in, connect to the local wireless connection and use Firefox as she is used to do. I just don't know how to do it, since or she enters her password at login, or she enter the password for the keyring (in order to connect to the local wifi).

Any ideas how I should proceed to make such an easy computing experience for her?

There should be, as this is Linux for human beings... she definitely is human, but as non-geek as a human can be :P

Any other suggestions for a easy, smooth and pleasant experience for non-geek humans on Ubuntu?

Thanks!

---

### Post by Dark_Stang on 2011-03-28
Well, you have three options really. Two of which you've already listed.
1. Have her enter her password at login.
2. Have her auto-login but enter her keyring password.
3. Leave her keyring password blank and enable auto-login.

That later will definitely be the easiest, but then all keyring passwords will be stored as plain text. Not the greatest security policy. 

Really she should only need to enter her user password if she's logging in for the first time or installing software/updates. And you can turn off automatic update checking.

---

### Post by ursoouindio on 2011-03-28
> **Dark_Stang said:**
> Well, you have three options really. Two of which you've already listed.
1. Have her enter her password at login.
2. Have her auto-login but enter her keyring password.
3. Leave her keyring password blank and enable auto-login.

That later will definitely be the easiest, but then all keyring passwords will be stored as plain text. Not the greatest security policy. 

Really she should only need to enter her user password if she's logging in for the first time or installing software/updates. And you can turn off automatic update checking.

Thanks for the reply, Dark_Stang!

Really, security is not the problem here. It's just a laptop for a mom to check her emails.

I set keyring password to *blank* and it stopped asking for it. Genial!

I know she would still need to input her password at certain occasions (like when the weekly scheduled update :D), but that should be easier for her to understand.

And, just wondering, isn't it possible for her to never need a password, is it?

---

### Post by Dark_Stang on 2011-03-28
I suppose you could set her user password to a blank password, using the command passwd. It will still prompt for her to enter her password for things, she just won't need to enter anything.

---

### Post by ursoouindio on 2011-03-28
ok, thanks. If so, I rather let her pick an password for her, it should make more sense.

---

### Post by Peter09 on 2011-03-28
You should be able to set it up so that she never needs a password for normal 'user' operations. 
 
If you can get to her machine regularly set yourself up as an Admin user and regularly login to do any admin tasks.

---

### Post by fabricator4 on 2011-03-28
> **Peter09 said:**
> You should be able to set it up so that she never needs a password for normal 'user' operations. 
 
If you can get to her machine regularly set yourself up as an Admin user and regularly login to do any admin tasks.

Absolutely!  You mother's login should not be the default Administrative User, since as Peter has pointed out, you're setting everything up to never ask for a password.

You'll have to take over the administrative tasks like updates yourself. Set your mother up with a basic Desktop User account - it will be much safer this way.

You might also do some checking and make sure there's no open ports that could be a point of attack.  Maybe disable SSH completely and so on. 

Chris.

---

### Post by ursoouindio on 2011-03-28
> **Peter09 said:**
> You should be able to set it up so that she never needs a password for normal 'user' operations. 
 
If you can get to her machine regularly set yourself up as an Admin user and regularly login to do any admin tasks.

Thanks for the suggestion, Peter, and also for the further thoughts, fabricator4.

That's a pretty good idea to handle security.

But, I don't live at the same place as here, in fact I just come once evey month, if so. I'm not a bad son, it's just a matter of distance and few time :P

So... I was thinking on eventually maintaining her laptop remotely. I tried here to manipulate her desktop through mine with "Remote Desktop" and that was pretty easy, but I'm afraid that once I return to my place (and of course left the local network) I would lose that possibility. Is it right?
Or I actually can connect from any place if I get her IP?
And, if so, what's the friendliest to get the actual IP? :P

---

### Post by fabricator4 on 2011-03-28
> **ursoouindio said:**
> I would lose that possibility. Is it right?

Down the street or across the continent, I don't think it really matters.

> 
And, if so, what's the friendliest to get the actual IP? :P

Setup a favourite (on her machine) for [http://echoip.com/](http://echoip.com/)

;-)

---

### Post by ursoouindio on 2011-03-28
thanks, fabricator4 :)

That should do it.

---

### Post by ursoouindio on 2011-03-28
Actually, I am at my place right now and tried to make a remote connection with hers laptop, using "Remote Desktop Viewer".

But I couldn't connect, I got the following message:

Connection to host 1##.##.##.### was closed.

---

