---
title: "RPCNET.EXE//LoJack?"
date: 2011-11-20
forum: General Help
---

### Post by rizzle-o on 2011-11-20
Hello fellow Linux users!

I am a noob, I have light experience with Linux from college but my knowledge is not that great on the subject.

I purchased an ACER Aspire 5742 last year from WalMart, and right from day one AVG was telling me about RPCNET.EXE, a Google search reviled it is apparently lo-jack software built into the BIOS and others have had this "issue" as well. 

Anyway....I got sick of seeing it every day, as it makes me feel my computer is not safe (even though I'm sure it is fine, and this is just a false positive.)

So I switched to ubuntu from windows 7, so, that being said, as this "software" is in my bios, and I am only running ubuntu currently, so if it is malicious in some way will it be able to affect my computer? Is my machine safe to use? I know, its a foolish question but any help would be great. 

Thanks!
Rizzle.

---

### Post by Dangertux on 2011-11-20
> **rizzle-o said:**
> Hello fellow Linux users!

I am a noob, I have light experience with Linux from college but my knowledge is not that great on the subject.

I purchased an ACER Aspire 5742 last year from WalMart, and right from day one AVG was telling me about RPCNET.EXE, a Google search reviled it is apparently lo-jack software built into the BIOS and others have had this "issue" as well. 

Anyway....I got sick of seeing it every day, as it makes me feel my computer is not safe (even though I'm sure it is fine, and this is just a false positive.)

So I switched to ubuntu from windows 7, so, that being said, as this "software" is in my bios, and I am only running ubuntu currently, so if it is malicious in some way will it be able to affect my computer? Is my machine safe to use? I know, its a foolish question but any help would be great. 

Thanks!
Rizzle.

From a security standpoint your system was never compromised, rpcnet.exe is a system tracking process designed to aid in the even of laptop theft (suffice it to say it doesn't work very well.)

That being said, the software itself is not in the BIOS, it reads data out of the BIOS to confirm laptop identity (IE: that the BIOS are that of the computer it was installed on). And will not affect Ubuntu as it was not propegated from the BIOS but installed in Windows.

Hope this helps.

---

### Post by rizzle-o on 2011-11-20
I called Acer, and they had no clue what I was talking about and gave me a 1800 number, I called that and they told me it was a Trojan attached to my bios and that a simple DBAN and reinstall of the orig O.S. would not work (as it would just copy back into the HDD anyway), and for 99 dollars they would "walk me through" the removal over the phone. Acer also claims none of their laptops come with lojack, even though on Absoloute Software's website, it lists Acer as a partner (along with Dell/Gateway...) which adds to my confusion. AVG sees it as malicious, which is cause for concern to me as I own one computer, and I enter a lot of personal information on it. I appreciate your help. And honestly. I am really liking 11.10 compared to Win7.

---

### Post by Dangertux on 2011-11-20
> **rizzle-o said:**
> I called Acer, and they had no clue what I was talking about and gave me a 1800 number, I called that and they told me it was a Trojan attached to my bios and that a simple DBAN and reinstall of the orig O.S. would not work (as it would just copy back into the HDD anyway), and for 99 dollars they would "walk me through" the removal over the phone. Acer also claims none of their laptops come with lojack, even though on Absoloute Software's website, it lists Acer as a partner (along with Dell/Gateway...) which adds to my confusion. AVG sees it as malicious, which is cause for concern to me as I own one computer, and I enter a lot of personal information on it. I appreciate your help. And honestly. I am really liking 11.10 compared to Win7.

I am not sure why Acer told you that as I know for  a fact it comes installed on their systems.  It can be removed, though not easily from the BIOS component. That being said it can not propagate from the BIOS to Ubuntu since it relies on hooking the Windows registry which you don't have in Ubuntu. Even still it is not malicious on nature and I wouldn't sweat it. 

If it makes you feel better I own a laptop that runs Linux and has the lojack bios component still and I don't think twice about it.

---

### Post by rizzle-o on 2011-11-20
Yeah, Acer doesn't want to talk unless you're willing to pay apparently. And they hook you by making you think you have an issue when you don't. Still, AVG should lower its sensitivity a bit to this, as it flags it every single time you scan, and it can't be removed. Thanks for the help, puts my mind at ease.

---

