---
title: "a question on bash script"
date: 2011-03-28
forum: General Help
---

### Post by volvolinux on 2011-03-28
Hello friends
 
I read a bash script, but I can't undestarnd some part. Hope you can help me :)
 
"$EASY_RSA/pkitool" --initca $*

if i run the script pkitool like this, i see I will pass "--initca" as the first shell parameter, but what does the "$*" do?

---

### Post by gzarkadas on 2011-03-28
Passes all parameters given to containing script as the rest (after --initca) arguments of the called (sub)script.

See: [http://www.gnu.org/software/bash/manual/bash.html#Special-Parameters](http://www.gnu.org/software/bash/manual/bash.html#Special-Parameters)
Also: type `info bash'  in a terminal window.

If you plan to delve serioulsy into shell scripting, I suggest your read it all.

---

