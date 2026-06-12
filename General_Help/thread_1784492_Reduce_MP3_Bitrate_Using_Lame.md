---
title: "Reduce MP3 Bitrate Using Lame"
date: 2011-06-17
forum: General Help
---

### Post by sillywindows on 2011-06-17
Hi All,

I am wanting to reduce around 9.9gigs of music to 8gigs to fit on my phone. I have done some snooping and noticed a program called Lame. I also noticed a code:
[COLOR=Blue]
[/COLOR][COLOR=Blue]for x in [ `ls -1 *.mp3` ]; do lame --preset 32 $x new32-${x}; done

[COLOR=Black]I was wondering if someone would be able to explain the code and how I go about converting the bitrate to 96?

Thanks ;)

*Bonus Questions:*
Will it be possible to convert them all at once? Is my goal of 8gigs reachable with 96bitrate?
[/COLOR][/COLOR]

---

### Post by andrew.46 on 2011-06-17
I guess for a really simple reduction something like the following would be a start:

```

for f in *.mp3
  do 
 lame -V 7 "$f" "${f%.mp3}_100.mp3"
done

```

This is a 'for' loop and many of the gruesome details can be seen in the bash man pages, suffice it to say that this small loop will look for mp3 files in the working directory and convert them to [about 100kbps]("http://wiki.hydrogenaudio.org/index.php?title=Recommended_LAME#Technical_information") and name the output file slightly differently to the input file. Perhaps grab a few mp3s and place them in a single directory to test this loop and see if it is what you are after? All settings can be altered to fit your needs...

---

