---
title: "Confusion about the &quot;Restricted&quot; repository"
date: 2009-09-24
forum: General Help
---

### Post by Missing_Number on 2009-09-24
Exactly how "legal" is it to use software in the restricted repository?  I looked it up, and it said it's illegal in "some countries" without listing the countries specifically.  

I live in the United States of America.  Can someone tell me the legality of using this repository specifically the Ubuntu Restricted Extras?

---

### Post by doas777 on 2009-09-24
> **Missing_Number said:**
> Exactly how "legal" is it to use software in the restricted repository?  I looked it up, and it said it's illegal in "some countries" without listing the countries specifically.  

I live in the United States of America.  Can someone tell me the legality of using this repository specifically the Ubuntu Restricted Extras?

you will have to contact legal representation in each of those jurisdictions. what is legal today may not be tommorow and vice versa. No one could make a solid determination either way. 

in the long run, you are not in any particular danger. that the restricteds are not in the core gives cannonical an easy way out, since it was our explicit decision to use them, but MS can't really come after you personally to extract licensing costs for a wmv codec.

---

### Post by solitaire on 2009-09-24
It's bascially things like DVD codecs. Which is closed source and is under some sort of copyright or required a licence fee to use. They have been ported to Linux by various methods but are in a "gray Area" when it comes to actually owning it without paying the license holders who created the software in the first place.

And things like encryption software is also in restricted due to the fact it my be illegal to export/import or own strong encryption in some countries...

Although the police and lawyers won't crash through your door as soon as you play a DVD in Linux, it's still technically illegal therefore you could get into trouble...

The community marks them as "Restricted" so that you know it's on your own head if you use them in a country where you may get into trouble...


Others may give a better explanation...

---

### Post by CatKiller on 2009-09-24
> **solitaire said:**
> It's bascially things like DVD codecs. Which is closed source and is under some sort of copyright or required a licence fee to use. 

It's not copyright that's the (legal) problem*, *it's patents. The use of certain algorithms is illegal in some countries since the government has seen fit to grant monopolies on them. If you live in one of those countries where software patents are granted, you will need a license from the patent holder to be able to do those sums. It's insane, but that's the law. To establish accurately whether that applies to you, you will need to consult a patent lawyer, as doas777 says; the opinion of some random person on the Internet is no kind of legal defence.

The other big one is specifically playback of encrypted DVDs. The DMCA and similar legislation in other countries makes it illegal to circumvent the "technical protection methods" - CSS in this case - even if the use is "fair."

The USA is the worst offender in both these respects, but other countries are pretty bad too. The only legal solutions are to either get a [licence]("http://shop.canonical.com/index.php?cPath=19&currency=USD") or a better government.

The other class of problematic software, as solitaire alludes to, is proprietary software. This is perfectly fine to use, but Canonical are not allowed to distribute it to anyone. The "restricted" status isn't to protect you, it's to protect Canonical. An example of this is the Flash plugin; it is free to use but not to modify or redistribute. The package that you get from the Ubuntu repositories and "install" is simply a script that downloads the latest version from Adobe's own servers and installs that instead.

---

### Post by Missing_Number on 2009-09-24
Yeah... the M$ patent crap is pretty stupid.  I mean, some good came of it.  Micro$oft became a monopoly because the general consumer wanted one OS that could handle any kind of software or hardware without driver issues or incompatibilities.  The market chose Micro$oft.

I was unaware of the depth of the situation.  I thank you all for answering the best that you can.  Just one last question: where would I be able to contact such a lawyer?  It's ridiculous that I should have to PAY MONEY to know what parts of the "restricted software" package I'm allowed to use legally. 

It would be really helpful if Canonical could just get a patent lawyer to spell it out in plain English (or whatever) what you are and aren't allowed to use based on the country you live in.  But then again, the "restricted" repository is just there to cover their own asses...

Maybe I should try a distribution that's free as in freedom... when I'm more experienced.

---

### Post by redmk2 on 2009-09-24
> **Missing_Number said:**
> ...

Maybe I should try a distribution that's free as in freedom... when I'm more experienced.

That would be Debian.  You don't need to be anymore experienced than you are today.

The restricted repos are part of what make Ubuntu different from plain old Debian.  Most of it is the same.

---

### Post by CatKiller on 2009-09-25
> **Missing_Number said:**
>  Just one last question: where would I be able to contact such a lawyer?  It's ridiculous that I should have to PAY MONEY to know what parts of the "restricted software" package I'm allowed to use legally. 

Your government, mate. Just get a licence.

> It would be really helpful if Canonical could just get a patent lawyer to spell it out in plain English (or whatever) what you are and aren't allowed to use based on the country you live in. 

And what if they got it wrong? You're expected to know the law in your own country. That's hardly Canonical's fault. They've made the licences easy to get hold of.

> But then again, the "restricted" repository is just there to cover their own asses...

Maybe I should try a distribution that's free as in freedom... when I'm more experienced.

Or you could just not install anything from the Multiverse repository. That's why it's separate.

---

### Post by mcduck on 2009-09-25
> **Missing_Number said:**
> 
Maybe I should try a distribution that's free as in freedom... when I'm more experienced.

As long as you don't use anything from the "restricted" (or similar) repository that's what you already get.

Ubuntu *is* free as in freedom, but allows you to make it something else if you want.

---

### Post by sliketymo on 2009-09-25
> **Missing_Number said:**
> Yeah... the M$ patent crap is pretty stupid.  I mean, some good came of it.  Micro$oft became a monopoly because the general consumer wanted one OS that could handle any kind of software or hardware without driver issues or incompatibilities.  The market chose Micro$oft.

I was unaware of the depth of the situation.  I thank you all for answering the best that you can.  Just one last question: where would I be able to contact such a lawyer?  It's ridiculous that I should have to PAY MONEY to know what parts of the "restricted software" package I'm allowed to use legally. 

It would be really helpful if Canonical could just get a patent lawyer to spell it out in plain English (or whatever) what you are and aren't allowed to use based on the country you live in.  But then again, the "restricted" repository is just there to cover their own asses...

Maybe I should try a distribution that's free as in freedom... when I'm more experienced.

:guitar:gNewSense.org, .Based on 8.04 Hardy.Embrace the Freedom my friend!

---

### Post by t0p on 2009-09-25
> **Missing_Number said:**
> 
I was unaware of the depth of the situation.  I thank you all for answering the best that you can.  Just one last question: where would I be able to contact such a lawyer?  It's ridiculous that I should have to PAY MONEY to know what parts of the "restricted software" package I'm allowed to use legally. 

So you want free legal advice?  Well, the internet is certainly the place to get it.  Unfortunately, the advice will be worth exactly what it cost you: nothing.

If you want to sleep with an easy conscience (and if this petty stuff actually does keep you up at night...) then you'll just have to break open your piggy bank and fork over the readies.  And why shouldn't you?  Your the one who wants to use software clearly marked "restricted".

> **Missing_Number said:**
> 
It would be really helpful if Canonical could just get a patent lawyer to spell it out in plain English (or whatever) what you are and aren't allowed to use based on the country you live in.  But then again, the "restricted" repository is just there to cover their own asses...


Indeed.  Canonical have given you advice.  Use the stuff at your own risk.

Why should a British company give legal advice to Americans anyway?   I'm sure their lawyers have their hands full advising their employer on UK law.  And you don't pay their wages.

> **Missing_Number said:**
> 
Maybe I should try a distribution that's free as in freedom... when I'm more experienced.

But you *are* using a Free distro.  Just don't install any of the non-Free stuff.  It's all clearly marked.

Using Debian isn't going to protect you if you insist on installing restricted software.

Alternatively you could just quit worrying about this nickel-and-dime stuff.  No one's going to come after you for installing restricted software.

Disclaimer: IANAL etc...

---

### Post by P4man on 2009-09-25
> **t0p said:**
> So you want free legal advice?  Well, the internet is certainly the place to get it.  Unfortunately, the advice will be worth exactly what it cost you: nothing.

The OP has a valid point. It would be nice to see some more info on what is assumed to be (il)legal where, as well as how to legalize it. I see everyone post "buy a license", but assuming downloading the MP3 codec is illegal where I live (and I have no idea if it is) how would I, as an individual, go about buying a license if I wanted to?

---

### Post by mcduck on 2009-09-25
> **P4man said:**
> The OP has a valid point. It would be nice to see some more info on what is assumed to be (il)legal where, as well as how to legalize it. I see everyone post "buy a license", but assuming downloading the MP3 codec is illegal where I live (and I have no idea if it is) how would I, as an individual, go about buying a license if I wanted to?

You can buy some legal Gstreamer codecs from Fluendo: [http://www.fluendo.com/shop/category/end-user-products/]("http://www.fluendo.com/shop/category/end-user-products/")

This is a nice option for those living in US who need these codecs but don't want to install the "restricted" ones..

---

### Post by 3rdalbum on 2009-09-25
> **mcduck said:**
> You can buy some legal Gstreamer codecs from Fluendo: [http://www.fluendo.com/shop/category/end-user-products/]("http://www.fluendo.com/shop/category/end-user-products/")

This is a nice option for those living in US who need these codecs but don't want to install the "restricted" ones..

Better yet, get them straight from Canonical's shop; they are cheaper and you can buy LinDVD while you're there.

---

### Post by keastes on 2009-09-25
one thing not being touched on here is this, what if i have a licence for this because i dual/tri-boot (OSX/)windoze/linux and have on windoze/OSX/other linux, do i have to shell out riduculus amounts of money to be able to listen to music or watch a DVD while doing whatever i do in soley (ow, can't spell) in linux for what ever reason?:confused:


god bless america we need it.

---

### Post by doas777 on 2009-09-25
one thing to consider is that many of the legally grey areas of codec development are still grey legally because no one has ever tested them in front of a judge. no fitting precedents, or judges interpretations to fall back on. the lawyers themselves don't know how the case would come out.

---

### Post by grndplane on 2009-09-25
You could just install Mint Linux which is built from Ubuntu with all the codecs and programs.

---

### Post by mcduck on 2009-09-25
> **grndplane said:**
> You could just install Mint Linux which is built from Ubuntu with all the codecs and programs.

That won't change anything, really. The codecs are still in the gray zone, no matter if they come preinstalled or if you install them yourself.

---

### Post by P4man on 2009-09-25
> **mcduck said:**
> That won't change anything, really. The codecs are still in the gray zone, no matter if they come preinstalled or if you install them yourself.

It might change who's liable though?
I dont know what disclaimer they have on Mint's website about this (quick look: not much), or how much it would matter.. but (extreme example) if I buy an MP3 player from some taiwanese company that didn't buy a license, i can't imagine I could be held liable for buying it in good faith. Likewise I wonder if an ordinary user could be expected to know if downloading mint linux could possibly be illegal. At least when you enable the multiverse, there is *some* warning

---

