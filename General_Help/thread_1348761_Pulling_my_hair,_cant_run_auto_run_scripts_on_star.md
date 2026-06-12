---
title: "Pulling my hair, cant run auto run scripts on start up!"
date: 2009-12-07
forum: General Help
---

### Post by mac666 on 2009-12-07
Hey
Im in a bit of trouble;

I have some ".sh" scripts that needs to be ran inside an terminal on start up.
And i cant really get it to work.

ive tried
xterm -e ./home/bla/test.sh , etc. but it doesnt work.

Any ideas? The script never runs when i try my weird combos... Please help!

---

### Post by t0p on 2009-12-07
Have you tried just putting '/home/blah/script.sh' in as a start-up command?

---

### Post by ankspo71 on 2009-12-07
Hi, 
I do like the above posters command...

go to system > preferences > Startup Applications, then add the following:  <--- nevermind this part, I just saw you are using xubuntu.

sh /home/blah/script.sh 
or if you prefer/require bash...
bash /home/blah/script.sh  

James

---

