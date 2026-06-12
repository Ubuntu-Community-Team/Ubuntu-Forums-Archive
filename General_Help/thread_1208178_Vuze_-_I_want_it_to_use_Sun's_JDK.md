---
title: "Vuze - I want it to use Sun's JDK"
date: 2009-07-08
forum: General Help
---

### Post by NovaAesa on 2009-07-08
Hi all,

I just installed Vuze from the repos, but it's not working:
```

ps@ps-compaq-presario:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found

```
Obviously I don't have the java open JDK installed. I do however have the Sun JDK installed. I would like to configure Vuze to use the Sun JDK so that I only need to have to have one JDK installed. But I have no idea how to change which JDK is used without actually opening Vuze itself.

If someone could give me any tips on how to change the JDK used, that would be excellent.

Cheers,
-Nova

---

### Post by synapsys on 2009-07-08
Are you really sure you want to use Vuze? I've had many many problems with it. I use Deluge instead... much much better imho.

Anyways, if you MUST use vuze, you could try making a symbolic link from the file it's looking for to the file you want.

---

### Post by QIII on 2009-07-08
I take it you have probably already done something like this:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk

Now 

sudo update-java-alternatives -s java-6-sun

which should change the preferred JDK to Sun.

Your mileage may vary, of course.

---

### Post by NovaAesa on 2009-07-09
> **synapsys said:**
> Are you really sure you want to use Vuze?Well, I want to at least use something with a scheduler. Deluge doesn't have one which makes it somewhat useless for my needs.

> Anyways, if you MUST use vuze, you could try making a symbolic link from the file it's looking for to the file you want.
I'll give that a try tonight =]

[quote=QIII]Your mileage may vary, of course.[/quote]Yes, it did vary unfortunately. Same error message as before.


Thanks for the help everyone, I'll work out how to make a symbolic link tonight, post back the results. In the meantime, if anyone knows of a bittorrent client with a scheduler, please tell me!

thx

---

### Post by QIII on 2009-07-09
If you got the same message, then I suspect that vuse itself is looking for OpenJDK specifically by default.

It might be worth installing OpenJDK to get vuse running, then seeing if there is some configuration available once you have it running to change to Sun.

---

### Post by NovaAesa on 2009-07-11
Thanks for the help all. I found out that Transmission actually has a crude (but good enough for my purposes) built in scheduler. Looks like I'll be using it rather than Vuze.

Cheers.

---

