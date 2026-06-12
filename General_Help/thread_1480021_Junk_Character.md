---
title: "Junk Character"
date: 2010-05-11
forum: General Help
---

### Post by killthemyth on 2010-05-11
Chinà&#65533;with involvement

Hi all, 

I'm working  from the last night and still unable to remove this junk character. I tried to see the output of the octal value of the junk character but unable to find it. it tried ob -o filename.

0000000 103 150 151 156 303 240 302 240 167 151 164 150 040 151 156 166
0000020 157 154 166 145 155 145 156 164 012
0000031

then I tried removing by using tr command. But unable to do so. 

I'll be very thankful if you kindly help me as i m stuck in my project. Please help.
Other code in awk, sed or shell script is utmost welcome.

Thanks once again,

---

### Post by lmarmisa on 2010-05-11
Maybe you need a hex editor like Ghex.

Open Synaptic (System -> Administration -> Synaptic Package Manager) and install ghex.

Open GHex selecting Applications -> Programming -> Hex editor.

Best regards,

Luis

---

### Post by killthemyth on 2010-05-11
Hi very thanks..
I figured out the octal no, but the problem is still unsolved. the word à is made of two octal no viz '\303' and '\240' and the junk character is made of '\302' and '\240'

Now what I can use command tr to remove both the octal set '\302' and '\240' but it also remove the '\240' but it also remove the one of , which I don't want 

Any soln.. ??

Thnks in advance

---

