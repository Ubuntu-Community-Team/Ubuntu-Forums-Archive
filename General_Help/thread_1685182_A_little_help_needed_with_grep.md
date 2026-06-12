---
title: "A little help needed with grep"
date: 2011-02-10
forum: General Help
---

### Post by AnRkey on 2011-02-10
[LEFT]Hi everyone,

I am automating the signing of my DNSSEC zones in bind and I have hit a small snag with grep.

My script outputs the following so far.

```
Kanrkey.ubuntu-user.com.+157+11286
Key: xlr27lbsLDYoUH4OEbcR/mULzNPhJmAQO+KB2pDy67X4zs/aeMBkcvovfiTs0ekgMOPrDhGtZoDZdWrlBlKbjA==
```So far I'm getting this output by using this
```
cat ./Kanrkey.ubuntu-user.com.*.private | grep Key:
```Can anyone tell me how to get more chopped off so that my output reads as follows?
```
anrkey.ubuntu-user.com
xlr27lbsLDYoUH4OEbcR/mULzNPhJmAQO+KB2pDy67X4zs/aeMBkcvovfiTs0ekgMOPrDhGtZoDZdWrlBlKbjA==
```Any help would be cool,

R
[/LEFT]

---

### Post by Habitual on 2011-02-10
Skip the cat and use
```
grep Key ./Kanrkey.ubuntu-user.com.*.private | cut -d: -f2-
```

---

### Post by AnRkey on 2011-02-11
> **Habitual said:**
> Skip the cat and use
```
grep Key ./Kanrkey.ubuntu-user.com.*.private | cut -d: -f2-
```

I'm getting closer. The output is now this:

```
Kjohn.bondsai.co.za.+157+16915
 cOZX8I15tqNZTVOZiSEcgLC305bC+IFTUnR7ODnre//3H91+Ya0Xji+a9QDihl6xEb6ARfenSeiNLDWWUzbzjA==
```I like the idea of leaving cat out of it. Now I just need to get the space out from in front of the key and the K chopped of from the front of the domain name. The last worry will be to chop off the bit after and including the .+1... at the end.

There is this tool in Mikrotik's RouterOS called pick. Pick is handy becuase it lets you choose data from a string x characters after the first and y characters before the end. Handy for choosing text out of a string if you know it's position in that string.

Pick with grep would have been awesome. Any ideas on how to use cut in this way?

Thanks for your help so far,

R

---

### Post by Habitual on 2011-02-11
Ya, I saw the space too, but I left that that up to you to decide.
```

grep Key file | sed -e 's/Key: //g'
```

does it.

another more "elegant" solution may exist. I'm just a hack. :)

and here it is:
```
grep Key x | cut -c 6-
```

I love linux. Freedom to choose.

HTH.

I knew an Anarchy from South Africa Years ago on irc.
But I don't think he'd be asking this type of Question, but who knows?
I only "knew" him on IRC.

dbCooper
==-Phrozen4Life==-

---

### Post by aeiah on 2011-02-11
i guess the relevant thing to take from this is that you were struggling with grep because you were only thinking of using grep. grep does things with lines, and you needed something that manipulated the line after grep parsed it. one of the great things with linux and its tools is how well they work together with pipes, and that there are many ways to skin a cat.

for what its worth, id have used trim (tr). tr is also handy for find and replace stuff, and not just deletions.

```

grep Key ./Kanrkey.ubuntu-user.com.*.private | tr -d 'Key: '

```

---

### Post by AnRkey on 2011-02-11
> **aeiah said:**
> i guess the relevant thing to take from this is that you were struggling with grep because you were only thinking of using grep. grep does things with lines, and you needed something that manipulated the line after grep parsed it. one of the great things with linux and its tools is how well they work together with pipes, and that there are many ways to skin a cat.

for what its worth, id have used trim (tr). tr is also handy for find and replace stuff, and not just deletions.

```

grep Key ./Kanrkey.ubuntu-user.com.*.private | tr -d 'Key: '

```

Pretty much exactly what he said yes :)

tr is one sexy little tool to have in one's aresonal. 

Thanks guys ;)

PS: it's me yes R from George ZA, is this really a noob question? **bows head in shame**

---

### Post by AnRkey on 2011-02-11
Wow, this trim (tr) is friggen awesome, it's like christmas baby. The wholy friggen grale of stdout manipulation. I mean with this and good old sed, u'r set! Now if I can just figure out awk's latin...

Thanks again guys!

---

### Post by Habitual on 2011-02-11
Glad it is working out for you.

woof

---

