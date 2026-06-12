---
title: "[Jaunty]: my browsers are not loading several pages... hotmail, megaupload, forums"
date: 2009-08-24
forum: General Help
---

### Post by nachoparker on 2009-08-24
Hello,

I have an AMD64 with Ubuntu Jaunty, and since last week I haven't been able to use certain websites like hotmail, and others like megaupload or some forums don't respond when I introduce queries (either the captcha or the message).

I have the same problem with firefox 3.0,3.5 and konqueror.

My other computer with Hardy firefox 3.0 and my room mate's computer with Hardy firefox 3.5, and sea monkey work perfectly so I don't think it is the router or a bug in the browser.

I suspect my system is not working with php somehow.

I tried completely removing and reinstalling firefox and xul-runner, and I also tried a clean session without extensions with -profilemanager, cleaning all cookies, session info and cache

Please, any hint?

---

### Post by exutable on 2009-08-24
Don't really know what's going on but have you tried something like Opera or Chrome in an attempt to narrow it down?

---

### Post by nachoparker on 2009-08-24
Thanks for your suggestion, but as far as I know there are not such versions for linux

I suspect something is corrupted but I don't know what, since a black out last week

I have tried a couple of browsers  already as I said and tried reinstalling but no luck

Any help greatly appreciated

---

### Post by nachoparker on 2009-08-24
another curious thing, I can log in this forum but not post

it stays waiting forever until it times out like with the other pages with problems

---

### Post by SunnyRabbiera on 2009-08-24
> **nachoparker said:**
> Thanks for your suggestion, but as far as I know there are not such versions for linux

I suspect something is corrupted but I don't know what, since a black out last week

I have tried a couple of browsers  already as I said and tried reinstalling but no luck

Any help greatly appreciated

Opera has a linux version, its just not in the default repositories.
Personally this sounds like a connection issue of some kind, just because one computer is working fine doesnt mean all will.

---

### Post by P4man on 2009-08-24
can it be http**s** protocols arent working?
Not that Id have a solution :s

perhaps you can try running

firefox -profilemanager

and create a new profile, see if that helps? Although granted, i dont see why Konquerer wouldnt work either then.

---

### Post by exutable on 2009-08-24
and Chrome just came out in 64-bit version

---

### Post by nachoparker on 2009-08-24
> **P4man said:**
> can it be http**s** protocols arent working?
Not that Id have a solution :s

perhaps you can try running

firefox -profilemanager

and create a new profile, see if that helps? Although granted, i dont see why Konquerer wouldnt work either then.

Thank all for the replies

Yeah,I think that is what happens, either the protocols or the network (router), but all other three computers in my house browse without problems, so I think it'd rather be the former.

I don't know how to check it though, or reinstall them, as I can navigate most pages, it's just when there is server activity, php and the like that it does not like it.

And it happens in all my browsers

I tried the profile manager already.

---

### Post by P4man on 2009-08-24
can you open this site ?

[https://launchpad.net/](https://launchpad.net/)

---

### Post by note32 on 2009-08-24
could try epiphany

---

### Post by nachoparker on 2009-08-24
> **P4man said:**
> can you open this site ?

[https://launchpad.net/](https://launchpad.net/)

I can, I can also use google, wikipedia, wolfram...

---

### Post by P4man on 2009-08-24
so its not a problem with SSL encryption. Bummer. I guess Im now as stumped as you lol.

Give opera a try, just to see if the problem lies with the browser or somewhere deeper.

[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

---

### Post by nachoparker on 2009-08-24
Hello and thanks again

I tried epiphany and opera (wow its fast!)

epiphany the same as firefox and konqueror... no hotmail, no forum, no megaupload

surprisingly opera works for all those except for hotmail (never expected a microsoft product to be very compatible any way, though it was working so far)

so yeah, still puzzled but advancing

Yeah could be something to do with some security service? except for opera all browsers have the same simptoms and I have to say that the forum in opera works only some times, right now is not working

---

### Post by P4man on 2009-08-24
> **nachoparker said:**
> 
so yeah, still puzzled but advancing


Advancing? If anything, I understand even **less** now LOL. Is the hotmail site not loading at all in opera? It seems to work just fine here (although i got no hotmail account that i can remember heh)

---

### Post by nachoparker on 2009-08-24
nah, time out when I try to login, time out also when I introduce the captcha in megaupload and in the forum when I try to publish

MU always works in opera

---

### Post by nachoparker on 2009-08-24
another thing, the forum does not actually always time out in firefox 3.0, if I wait like 3 minutes it asks me where to save the php file

??????

---

### Post by P4man on 2009-08-24
> **nachoparker said:**
> another thing, the forum does not actually always time out in firefox 3.0, if I wait like 3 minutes it asks me where to save the php file

??????

That at least is fairly "common". Not entirely sure what causes it, but when a server is too slow to respond, I also sometimes have seen that behaviour.

But lets see what happens when you click this link:

[http://65.54.186.17/](http://65.54.186.17/)

(its the MSN live login page

[http://login.live.com/](http://login.live.com/)
)

---

### Post by nachoparker on 2009-08-24
ok, if i click the url I get the usual

if I click the ip address I get

[COLOR="Red"]
Secure connection failed

62.54.186.17 uses an invalid security certificate. the certificate is only valid for login.live.com (error code:ssl_error_bad_cert_domain)[/COLOR]

Wow, that's sth!!

---

### Post by P4man on 2009-08-24
which browser(s) gave that error?

But indeed, at least now there is some progress, though Im at a loss why the browser complains about the ssl certificate, as its not used there yet?

Are you using some fancy firewall or some antivirus / security software that we should know about lol? A download accelerator that prefetches stuff? Im just guessing here, it really doesnt make any sense to me. Since im guessing, what DNS server do you use ? the same as on the other computers?

---

### Post by nachoparker on 2009-08-24
firefox 3.0

nah, no fancy firewall, anything... maybe I should check tomorrow the config of the router but I didn't change anything there

I am using the dns server from the ISP, the same as everyone else in the house.

---

### Post by nachoparker on 2009-08-25
anybody got a clue?

---

### Post by P4man on 2009-08-25
Not really no.
But hey, see what happens when you remove (or rename) the ~/.mozilla/firefox or (firefox-3.5) folders. If that doesnt help try running firefox as root with "gksudo firefox".

---

### Post by nachoparker on 2009-08-25
This is a test

---

### Post by nachoparker on 2009-08-25
okayyy

really getting there.. I renamed the folder as you suggested... megaupload and this forum work now... only hotmail and the other forum don't work...

yeah after all some file was corrupted on that black out

Same thing as a root. (I don't really care about hotmail... maybe it's something of incompatibility with jaunty, I don't use it much)

Thanks so much for your help

EDIT : in this forum I can only post very small messages,like 2 words

---

