---
title: "different results when running in command prompt and via script"
date: 2010-05-26
forum: General Help
---

### Post by ykk_five on 2010-05-26
hi all,
  i wonder if it is usual that the results of running commands via the command line is different from running them in a script file.

 my problem is that, i've to run 'modprobe -r e100' and 'modprobe e100' before suspend my machine via pmi in order to resume it properly. i wrote a script containg EXACTLY the same commands as i typed in the terminal/console but the result was not the same. the machine cannot be resumed as expected if i run the script file.

any idea please?

thx a lot

---

### Post by dino99 on 2010-05-26
googling around suspend, lot of users have found that was a special effect issue: so enable special effects then swith back to none (system pref appearance special effects)

---

### Post by ykk_five on 2010-05-26
thx for prompt reply

did u mean special effects in gnome? i even don have gnome running
i just executed the commands in tty1

edit: actually, i should say the resume is not 100% done due to unable to load e100 firmware if i run the script instead of typing the commands manually. that's why i wonder why the results were different

edit2: although the suspend funtion works now by putting the command elsewhere, still don understand what happened

---

