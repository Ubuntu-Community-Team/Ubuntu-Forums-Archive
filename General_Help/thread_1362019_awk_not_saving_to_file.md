---
title: "awk not saving to file"
date: 2009-12-22
forum: General Help
---

### Post by xzased on 2009-12-22
I have a script that basically reads a password from a file, and when it finishes it sets the password field back to the default name using awk. It prints the output on the screen but it doesnt actually save it to the file (password file is "pass" btw:

```
read -s -p "Enter Password for testuser1: " pass1
echo " "
read -s -p "Enter password for testuser2: " pass2
echo " "
sed -i 's/set1/'$pass1'/g' pass 
sed -i 's/set2/'$pass2'/g' pass

while read inputline
do
passuser="$(echo $inputline | cut -d: -f2)"
(echo $passuser; echo $passuser) | smbpasswd -s  tester
done < pass 

awk -F: -v OFS=: '{ $2 = "set1" }{ print }' pass 

```

So, on the last line awk should replace the pass field with "set1", but it is not saving it to the pass file. How can I make it save the changes to the file?

---

### Post by dcstar on 2009-12-22
> **xzased said:**
> I have a script that basically reads a password from a file, and when it finishes it sets the password field back to the default name using awk. It prints the output on the screen but it doesnt actually save it to the file (password file is "pass" btw:

```
read -s -p "Enter Password for testuser1: " pass1
echo " "
read -s -p "Enter password for testuser2: " pass2
echo " "
sed -i 's/set1/'$pass1'/g' pass 
sed -i 's/set2/'$pass2'/g' pass

while read inputline
do
passuser="$(echo $inputline | cut -d: -f2)"
(echo $passuser; echo $passuser) | smbpasswd -s  tester
done < pass 

awk -F: -v OFS=: '{ $2 = "set1" }{ print }' pass 

```

So, on the last line awk should replace the pass field with "set1", but it is not saving it to the pass file. How can I make it save the changes to the file?

Like all functions, you use ">" or ">>" to send output to a file.

---

### Post by xzased on 2009-12-22
nope, not working either. I tried:

```
awk -F: -v OFS=: '{ $2 = "set1" }{ print }' > pass 

```

```
awk -F: -v OFS=: '{ $2 = "set1" }{ print }' >> pass 

```

and the process just hangs

---

### Post by kaibob on 2009-12-22
I'm not an awk expert, but I don't think awk has anything comparable to the sed -i (edit file in place) option. So, I believe you have to use file > newfile at the end of the awk command.

---

