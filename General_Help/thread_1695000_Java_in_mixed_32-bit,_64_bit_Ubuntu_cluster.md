---
title: "Java in mixed 32-bit, 64 bit Ubuntu cluster"
date: 2011-02-25
forum: General Help
---

### Post by skthetwo on 2011-02-25
For parallel running, I cluster my 3 existing 32-bit-Ubuntu machines ( they've got less than 4Gb memory anyway)  via a program called Hadoop, and also some homegrown stuff. Essentially, my app's Java programs are machine level parallel, and get "thrown" to whichever machine is free and they run there.

Java is of course an interpreter.

I'm adding a 8Gb Athlon 64 machine to the mix, and wondering what the issues will be if I put 64-bit Ubuntu on it, and so bring that into the mix - specifically for my Java programs that will run on potentially any machine.

IMO, In theory and per the wiki, the Java program addressing is as per its own reference standard, independent of the machine architecture,  so the programs should just run in whichever Java-VM it lands in - depending on which machine + operating system it gets thrown to. 

In theory. In practice ?

---

### Post by skthetwo on 2011-03-12
Well replying to my self in case somebody else comes down this path - for a mixed 32-bit, 64 bit cluster Java isn't a problem but the nature of Hadoop IS  !

I was testing out a packaged app - blastx ( packaged at a Indiana Uni course ) and used Hadoop to distribute, as in send over to the other PCs, and run it across 4 nodes - the blastx package was a 64-bit compatible C program so it ran on two of my nodes - which are 64 bit just fine but failed on the two 32 bit ones - fails oddly but specifically it didn't say libx not found or stuff like that, just:

*Cannot execute a binary file.*

Took a little while to sort out.

Moral of the story - well I for one am pushing those two nodes up to 64 bit straight away.

---

