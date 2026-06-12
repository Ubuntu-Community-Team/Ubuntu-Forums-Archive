---
title: "Secure alternatives to Skype"
date: 2011-03-20
forum: General Help
---

### Post by siddartha on 2011-03-20
The first need is to have easy cross system compatibility. Meaning Windows included. Audio/Video would be a plus, but it is not a must.

I need something that goes through SSL or something like that and not in plain view.

---

### Post by Script Warlock on 2011-03-20
ekiga

---

### Post by Joe of loath on 2011-03-20
You can install an encryption plugin on pidgin, so all your messages are encrypted end to end. I don't know what you mean by 'plain view', but you can install a boss-button plugin, so that a certain keypress will hide all your windows.

---

### Post by siddartha on 2011-03-20
Encryption plugin means installing some ugly client like pidgin.

With other words something like https instead of http.

---

### Post by Joe of loath on 2011-03-20
I'm pretty sure skype is encrypted end to end anyway, actually.

---

### Post by abyrne on 2011-03-20
According to the [Skype Blog]("http://blogs.skype.com/security/2005/10/skype_security_and_encryption.html"): > Ever since Skype was launched, we have said it is, and will remain, secure. Your Skype-to-Skype calls, chats and other communications are end-to-end encryped.

Plus, Skype is P2P, which means all of your communications go straight from your computer to the recipient's computer. There is no Skype 'middle-man' central server.

---

### Post by siddartha on 2011-03-21
That's right. It's encrypted and it does p2p while having a decent client across platforms. On the other hand the newer versions can come with advertising and also some of the traffic can be routed through your connection which is a drag while on some public wifi. That's why I was looking for an alternative.

---

### Post by mastablasta on 2011-03-21
> **siddartha said:**
> Encryption plugin means installing some ugly client like pidgin.
 
With other words something like https instead of http.
 
i see that visual appearance of the client is important to you when you do voice and video chat. because when i chat in video/voice my client (skype) is usually a small icon in the panel.
 
Also there are themes for pidgin and as i know you can customize the look yourself if you would like it to look different.
 
Then again there is plent of the IMs out there. Search the software center for them you will find plenty.

---

### Post by siddartha on 2011-03-21
> **mastablasta said:**
> Then again there is plent of the IMs out there. Search the software center for them you will find plenty.

Thank you Einstein. I guess the thread was to motivate myself to search through a bunch of clones.

---

### Post by siddartha on 2011-03-27
Thanks for nothing.

Anyway, after personal research Jabber offers secure connections. Also, although closed source AIM and ICQ also do secure the traffic.

---

### Post by Joe of loath on 2011-03-27
> **siddartha said:**
> Thanks for nothing.

Chill out, dude. *rolls hir eyes*

We gave you some alternatives and you passed them off as 'ugly', so you might as well have done the research yourself anyway ;)

---

### Post by siddartha on 2011-03-27
> **Joe of loath said:**
> We gave you some alternatives and you passed them off as 'ugly', so you might as well have done the research yourself anyway ;)

Back in the days where RedHat was just born the open source community used to have people who did understood simple English. With the rise of cool and distros like Ubuntu the AOL crowd moved to the next thing that sounded "neat". I asked for some secure protocol and not a plugin which would be an alternative to Skype. You in particular said something about a plugin to a half baked app with a terrible interface anywhere where Gnome is not standard than you told me about Skype. Gee! Skype would be a nice alternative to Skype, right? So, yes, open source means you're all alone beyond something of the complexity of changing the background in KDE. Thank you for reminding me that.

---

### Post by Joe of loath on 2011-03-27
Oh, so you wanted a DE-independent client? Why didn't you say so? After that comment about simple English, too...

---

### Post by UnrealMiniMe on 2011-03-29
I came to this thread hoping to find an answer to the OP, because I'm wondering the same thing.  First I'll comment on Skype though, because it seems not everyone understands the privacy concerns regarding Skype.

To start off, there's a whole Wikipedia article on [Skype's security](https://secure.wikimedia.org/wikipedia/en/wiki/Skype_security).  From what I've read, Skype is encrypted, but it's not encrypted for the purpose of protecting user privacy.  Instead, it's encrypted to obfuscate Skype's proprietary protocol, and it tends to create privacy as a conveniently marketable byproduct.  However, that means there's no guarantee against a back door, and there's also no way to verify the implementation.

The Ekiga developers talked a bit about this in an interview a while back:
[http://www.freesoftwaremagazine.com/columns/interview_with_ekiga_developers](http://www.freesoftwaremagazine.com/columns/interview_with_ekiga_developers)

Here's a CNET article about Phil Zimmermann's Zfone/ZRTP:
[http://news.cnet.com/E-mail-security-hero-takes-on-VoIP/2100-7352_3-6105589.html?tag=nefd.top](http://news.cnet.com/E-mail-security-hero-takes-on-VoIP/2100-7352_3-6105589.html?tag=nefd.top)

There's an interesting paragraph at the bottom:
[QUOTE=Article]An [analysis](http://eng.soros.kg/functions/programs/publish/skypeeng) by computer scientist Simson Garfinkel says "it is impossible to validate the company's claims regarding encryption." A subsequent presentation ([click for PDF](http://www.secdev.org/conf/skype_BHEU06.handout.pdf)) at the BlackHat Europe conference in March said the right algorithms were being used, but that there's "no way" to know if a backdoor for eavesdropping exists.[/QUOTE]

In addition, an Austrian official fueled rumors of a back door a few years back.  [Here](http://www.theregister.co.uk/2008/07/25/skype_backdoor_rumours/) is a register.co.uk article on this, but there are lots of others out there as well.

Finally, length-preserving encryption has to be used very carefully for VOIP, because combining it with VBR codecs without padding - like Skype does - allows attackers to identify target phrases with an accuracy of 50% or even 90%, without a single voice sample from you in particular.  [Here](http://www.cs.unc.edu/~fabian/papers/oakland08.pdf) is the paper on that, and [here](https://www.privacyinternational.org/article/skype-called-answer-mounting-security-concerns) is the page where I found it.  [Here](http://blogs.computerworlduk.com/unscrewing-security/2011/03/skype-is-great-but-should-you-bet-your-freedom-on-its-security/index.htm) is another perspective on the Privacy International page.

Long story short, it's perfectly reasonable to mistrust Skype, and a free/open source alternative is desperately needed.  The Ekiga developers apparently understand the need for strong encryption, at least according to the above interview, but after several years they still haven't delivered on it.  Their roadmaps for versions 3.4 and 4.0 don't seem to indicate an imminent change either.

Anyway, back to the real thread topic:  **I just came across Jitsi tonight, and it looks very promising** (not sure if it combines VBR with length-preserving encryption without padding though).  I actually came to these forums to see if anyone else has been talking about it*, and to find out if there are any other options I'm missing.  In the meantime though, the OP might want to do some research on Jitsi as a free and cross-platform Skype alternative.  For starters, [here's the Wiki page](https://secure.wikimedia.org/wikipedia/en/wiki/Jitsi), and [here's the official site](http://www.jitsi.org/index.php/Main/HomePage).

*As it turns out, a forum search for the software turns up this post alone. :(

---

### Post by siddartha on 2011-03-29
> **UnrealMiniMe said:**
> *As it turns out, a forum search for the software turns up this post alone. :(

Thank you so much for your info. That is the kind of problem I have. It's amazing how these layers of ignorance protect the open source into staying entrenched into the IT Middle Ages. Glorifying a kernel that does its job with an impressive design and performance for 1962, having low multimedia support, etc. Myself I have set my goal low, very low, just text communication. And [jabber.org]("http://www.jabber.org/") does deliver going beyond SSL with TLS. Also it is interconectable with Google talk.

I have found for audio one solution would be not ekiga, but mumble. [It does has encryption as far as 2007]("http://sourceforge.net/blog/potm-200911/") (for open source that is revolutionary). And it is low latency, although I find it quite weird with its IRC like style. On the other hand it means excellent conferencing although it would be a pain to direct someone used with the recent solutions though.

What's even more weird is that in a world with Firesheep and the recent compromised security certificates, most people still dream state dystopias forgetting about the script kiddie next door.

---

### Post by UnrealMiniMe on 2011-03-30
> **siddartha said:**
> Thank you so much for your info. That is the kind of problem I have. It's amazing how these layers of ignorance protect the open source into staying entrenched into the IT Middle Ages. Glorifying a kernel that does its job with an impressive design and performance for 1962, having low multimedia support, etc. Myself I have set my goal low, very low, just text communication. And [jabber.org]("http://www.jabber.org/") does deliver going beyond SSL with TLS. Also it is interconectable with Google talk.

I have found for audio one solution would be not ekiga, but mumble. [It does has encryption as far as 2007]("http://sourceforge.net/blog/potm-200911/") (for open source that is revolutionary). And it is low latency, although I find it quite weird with its IRC like style. On the other hand it means excellent conferencing although it would be a pain to direct someone used with the recent solutions though.

What's even more weird is that in a world with Firesheep and the recent compromised security certificates, most people still dream state dystopias forgetting about the script kiddie next door.

Yeah, Mumble looks like a fantastic solution for both conference calls and gaming.  The developers put care into both latency and quality, and like Jabber and Jitsi it uses TLS (it also uses OCB-AES128 ).  I'm looking for secure video chat though, so I unfortunately had to cross that one off my list from the start. :-/

---

### Post by jonathan22 on 2011-05-14
> **UnrealMiniMe said:**
> 
Anyway, back to the real thread topic:  **I just came across Jitsi tonight, and it looks very promising** (not sure if it combines VBR with length-preserving encryption without padding though).  I actually came to these forums to see if anyone else has been talking about it*, and to find out if there are any other options I'm missing.  In the meantime though, the OP might want to do some research on Jitsi as a free and cross-platform Skype alternative.  For starters, [here's the Wiki page](https://secure.wikimedia.org/wikipedia/en/wiki/Jitsi), and [here's the official site](http://www.jitsi.org/index.php/Main/HomePage).

*As it turns out, a forum search for the software turns up this post alone. :(

How did you like Jitsi?  I'm about to try it myself.

---

### Post by mikewhatever on 2011-05-15
This is an interesting topic that, IMHO, doesn't get nearly as much attention as it should. I will also be testing Jitsi in a couple of days. It looks promising, and hopefully by the end of the year it will be out of beta.
I think the following clients also deserve attention:
[http://www.qutecom.com/](http://www.qutecom.com/)
[http://www.sflphone.com/features](http://www.sflphone.com/features)

---

### Post by Yeti can't ski on 2011-05-25
I am trying Jitsi, and it seems really great. Much simpler, faster and more stable than Ekiga.

It is also JAVA and multiplatform, which is great for me because I am planning to take on the immense task of convincing one wife, a mother, a mother-in-law and a sister (amounting to Ubuntu, LMDE, MacOS and WinXP) to abandon Skype. 

I would like, however, to make PC-to-phone calls with Jitsi. I know that it is possible to do so using sipgate: 

[http://comments.gmane.org/gmane.comp.voip.ser/39733]("http://comments.gmane.org/gmane.comp.voip.ser/39733")

But I didn't have any luck with my Diamondcard.us account (a happy inheritance from my Ekiga times).

I would like to use Jitsi to do the PSTN (PC-to-phone) calls through a new iptel.org SIP account (jitsi can't handle the SIP Ekiga account): 

[http://www.jitsi.org/index.php/Documentation/FAQ#ekiga.net]("http://www.jitsi.org/index.php/Documentation/FAQ#ekiga.net")

Any ideas? I am attaching a shot of iptel.org's configuration screent. Perhaps I should open a separate thread?

---

