---
title: "While Loop"
date: 2011-03-21
forum: General Help
---

### Post by Johann-1.0 on 2011-03-21
Hello Fellows. I'm requesting your help because I made a script and it doesn't exit from the while loop when the condition is true. Note, the "!" in the condition is there on purpose, it is not a mistake. The second while loop is the bad one.

Here the code (very help would be appreciated):

```

echo "Introduzca un nombre de directorio"

directorio=fdjsfjdsf
while (! test -d $directorio)
do
	echo "Por favor, introduzca un nombre válido de directorio o presione \"Ctrl + C\" para salir"
	
	read directorio
done



while (! test  "$respuesta" = "S" || "$respuesta" = "N")
do
	
	echo "¿Desea listar los directorios ocultos? S(s) o N(n)"
	
	read respuesta
	echo $respuesta
	case $respuesta in 
		"S")
			
			directoriooculto=".*"
			echo "Usted ha escogido ver los directorios ocultos"
		;;
		"s")
			
			directoriooculto=".*"
			echo "Usted ha escogido ver los directorios ocultos"
		;;
		"N")
			
			directoriooculto="*"
			echo "Usted ha escogido NO ver los directorios ocultos"
		;;		
		"n")
			
			directoriooculto="*"
			echo "Usted ha escogido NO ver los directorios ocultos"
		;;
		*)	
			respuesta=""
			echo "Por favor introduzca una respuesta válida o                   presione \"Ctrl + C\" para salir"
		;;
	esac
done
		
			
for filename in $directorio/$directoriooculto
do
	echo "$filename"
	echo $filename
	sleep 1
done

```
Thank you in advance

---

### Post by Lars Noodén on 2011-03-21
It's probably something like this instead

 test  "$respuesta" = "S" || test "$respuesta" = "N")

or this

 test  "$respuesta" = "S" && test "$respuesta" = "N")

---

### Post by arubislander on 2011-03-21
Your loop says to continue as long as respuesta is either not equal to 'S' or equal to 'N'. So the loop will be exited when respuesta is 'S' and not equal to 'N'. That collapses to exiting when respuest is 'S'. Is that your intention?

---

### Post by Johann-1.0 on 2011-03-21
> **arubislander said:**
> Your loop says to continue as long as respuesta is either not equal to 'S' or equal to 'N'. So the loop will be exited when respuesta is 'S' and not equal to 'N'. That collapses to exiting when respuest is 'S'. Is that your intention?
Thank you for answering. My intention is to exit the "while" loop when respuesta is S or respuesta is N. This is, as long as "respuesta" is different from S or N, it will keep looping.
Thanks a lot for trying to help.
I'm wondering if it is related with a syntax error in test section.

---

### Post by Johann-1.0 on 2011-03-21
> **Johann-1.0 said:**
> Thank you for answering. My intention is to exit the "while" loop when respuesta is S or respuesta is N. This is, as long as "respuesta" is different from S or N, it will keep looping.
Thanks a lot for trying to help.
I'm wondering if it is related with a syntax error in test section.
I tried item 6 in this post...but didn't work either :(

[http://mywiki.wooledge.org/BashPitfalls#A.5B_.24foo_.3D_.22bar.22_.5D]("http://mywiki.wooledge.org/BashPitfalls#A.5B_.24foo_.3D_.22bar.22_.5D")

---

### Post by Johann-1.0 on 2011-03-21
> **Johann-1.0 said:**
> Thank you for answering. My intention is to exit the "while" loop when respuesta is S or respuesta is N. This is, as long as "respuesta" is different from S or N, it will keep looping.
Thanks a lot for trying to help.
I'm wondering if it is related with a syntax error in test section.
I tried item 6 in this post...but didn't work either :(

[http://mywiki.wooledge.org/BashPitfalls#A.5B_.24foo_.3D_.22bar.22_.5D]("http://mywiki.wooledge.org/BashPitfalls#A.5B_.24foo_.3D_.22bar.22_.5D")

I tried commenting the second part of test section and it worked ok...definitely the problem is in "Or" syntax

---

### Post by Rhubarb on 2011-03-21
Your Condition logic isn't quite right, and you're missing a ")" try this:

```
#!/bin/bash
echo "Introduzca un nombre de directorio"

directorio=fdjsfjdsf
while (! test -d $directorio)
do
	echo "Por favor, introduzca un nombre válido de directorio o presione \"Ctrl + C\" para salir"
	
	read directorio
done



while (! ( test "$respuesta" = "S" || test "$respuesta" = "N") )
do
	
	echo "¿Desea listar los directorios ocultos? S(s) o N(n)"
	
	read respuesta
	echo $respuesta
	respuesta=`echo $respuesta | tr 'a-z' 'A-Z'`
	case $respuesta in 
		"S")
			
			directoriooculto=".*"
			echo "Usted ha escogido ver los directorios ocultos"
		;;
		"N")
			
			directoriooculto="*"
			echo "Usted ha escogido NO ver los directorios ocultos"
		;;		
		*)	
			respuesta=""
			echo "Por favor introduzca una respuesta válida o                   presione \"Ctrl + C\" para salir"
		;;
	esac
done
		
			
for filename in $directorio/$directoriooculto
do
	echo "$filename"
	echo $filename
	sleep 1
done
```

I've used the "tr" command to convert lower-case to UPPER-CASE, so it works with SsNn.

There are many ways of getting it to work, I've tried not to modify your work as much as possible.

Bash scripting can be fun :D

---

### Post by Johann-1.0 on 2011-03-21
> **Rhubarb said:**
> Your Condition logic isn't quite right, and you're missing a ")" try this:

```
#!/bin/bash
echo "Introduzca un nombre de directorio"

directorio=fdjsfjdsf
while (! test -d $directorio)
do
	echo "Por favor, introduzca un nombre válido de directorio o presione \"Ctrl + C\" para salir"
	
	read directorio
done



while (! ( test "$respuesta" = "S" || test "$respuesta" = "N") )
do
	
	echo "¿Desea listar los directorios ocultos? S(s) o N(n)"
	
	read respuesta
	echo $respuesta
	respuesta=`echo $respuesta | tr 'a-z' 'A-Z'`
	case $respuesta in 
		"S")
			
			directoriooculto=".*"
			echo "Usted ha escogido ver los directorios ocultos"
		;;
		"N")
			
			directoriooculto="*"
			echo "Usted ha escogido NO ver los directorios ocultos"
		;;		
		*)	
			respuesta=""
			echo "Por favor introduzca una respuesta válida o                   presione \"Ctrl + C\" para salir"
		;;
	esac
done
		
			
for filename in $directorio/$directoriooculto
do
	echo "$filename"
	echo $filename
	sleep 1
done
```

I've used the "tr" command to convert lower-case to UPPER-CASE, so it works with SsNn.

There are many ways of getting it to work, I've tried not to modify your work as much as possible.

Bash scripting can be fun :D
Ounstanding Man...it worked perfectly. Thanks a lot for the "tr tip". I'm just learning bash scripting.
Sincerely, thank you.

---

