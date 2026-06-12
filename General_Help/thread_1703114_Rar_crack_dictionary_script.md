---
title: "Rar crack dictionary script"
date: 2011-03-08
forum: General Help
---

### Post by Jimmy9pints on 2011-03-08
Hello Folks,

Before anybody says it, no, I am not doing anything illegal.

I have a problem. I have about 50 rar and zip files. Each of them are locked with one of four passwords. I know the passwords, but I don't know which password is for which archive. 

Since this is a repetitive task that I will have to do again in the future, I want to write a script (or find one) that will try each of the four passwords for all of the .rar or .zip files in a directory. 

I believe the technical term for this is "dictionary attack" - however, my dictionary would only contain 4 words. 

I know some rudimentary Python. Would it be best to use Python for this or would Bash (which I don't know at all) be more suitable. 

Does anybody know of a script/app that already does this? I am not interested in bruteforce solutions. 

Cheers for your help,

Jimmy.

---

### Post by saint2000 on 2011-03-19
I've got the same problem, I know the password, just unsure as to which one. Did you have any luck with this?

---

### Post by Jimmy9pints on 2011-03-27
Yes, I got a solution. Sorry for the slow reply. 

I found the solution here: [http://www.linuxquestions.org/questions/linux-software-2/bash-script-to-extract-multiple-files-with-password-855327/](http://www.linuxquestions.org/questions/linux-software-2/bash-script-to-extract-multiple-files-with-password-855327/)

Here's the bash script:

```
 #!/bin/bash -x

# PARA extraer de gigapedia en 7z

where=$(dirname "$@")
filename=$(basename "$@")
cd "$where"


LIST=$(ls *.7z)
PASSWORDS="gigapedia.com ebooksclub.org ebooksclub_org library.nu gigle.ws"
status="fail"

while [[ $status = "fail" ]]; do
for i in $LIST; do 
	echo "Archivo=$i"
      	for pass in $PASSWORDS; do 
	  echo "Clave=$pass"
	  7z -y -p"$pass" x "$i"
	    if [ $? != 0 ]; then
	      echo "$pass no funcionó con $i"
	      echo
	      echo
	      echo "__________________"
	      status="fail"
	    else
	      status="success"
	      break
	    fi
	done
   done
done

ogg123 /mnt/sda3/ANANKE/SCRIPTS/darwin/KDE-Im-Connection-Lost.ogg
kdialog --passivepopup "GIGA: Extracción finalizada"	
rm -f oe.txt
rm -f *.7z 
```

Hope that helps!

---

