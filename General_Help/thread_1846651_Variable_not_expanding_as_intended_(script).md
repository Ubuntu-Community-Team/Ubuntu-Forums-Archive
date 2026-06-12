---
title: "Variable not expanding as intended (script)"
date: 2011-09-19
forum: General Help
---

### Post by HereSomeHow on 2011-09-19
Hi, I'm stuck with a variable expansion not working the way I want in a bash script.

The script is as follows:

```
#!/bin/bash 

# Script "ROBOT" para envio de Correos por lote
# usando sendEmail
Ruta="/share/Temp/Publicaciones/Pool";
Trabajos="/home/e408084/tmp/Lote";

# Verificamos el semaforo, y en su caso lo encendemos...
if [ ! -f "/home/e408084/tmp/Semaforo2.txt" ]; then
 # No existe, lo creamos...
 ls * > "/home/e408084/tmp/Semaforo2.txt";

# Obtenemos los archivos a procesar...
ls "$Ruta"/*.job > "$Trabajos";

IFS=$'\n';
# Ahora ciclamos para enviar uno a uno los correos solicitados...
for trabajo in `cat "$Trabajos"`;
	do
		echo "Archivo a trabajar : $trabajo";
		Comando=`cat $trabajo`;
		echo "Enviando correo con : $Comando";
		sendEmail "$Comando";
		
		export Comando;
		
		rm "$trabajo";
		if [[ $Comando = *body* ]]; then 
			rm "${trabajo%job}body";
		fi
	done;

unset IFS;

# Nos deshacemos del archivo temporal...
if [ -f "$Trabajos" ]; then rm "$Trabajos"; fi
 # Y tambien del semaforo...
 rm "/home/e408084/tmp/Semaforo2.txt";
fi
```

Basically, it sends mails using sendEmail, and takes the parameters from files on a special directory. I've tried with different quoting, all to no avail. All I get is a message from sendEmail saying that "...<all the options>" is not a recognized option.

This a sample file content, with the addresses changed.
```

-t xxx@yyyy.com.mx -cc xxxx@gmail.com -u "A test" -m "Short title" -f zzzz@yyyy.com.mx -s wwww.mx.bsch

```

---

### Post by sisco311 on 2011-09-19
ls shows you a representation of files. They are NOT file names (for simple names, they mostly happen to be equivalent). Do NOT try to parse it. [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

Also check out BashPitfalls #1 (link in my signature).

Insead of *for i in `cat file`* use a while loop:
```
while read -r whatever
do
    :
done< file

```

And check out BashFAQ #20 (link in my signature).

I'd try something like:
```

find path/to/dir -maxdepth 1 -name \*.job -type f -print0 > file
...
while IFS= read -r -d '' trabajo
do
    whatever
done< file
```

EDIT: Not sure why do you save the file names in a file. If you don't have to save them in a file, then you can use a for loop:
```
for trabajo in *.job
do
    :
done
```

---

### Post by HereSomeHow on 2011-09-19
I send the list of files to a file so if new files are created while executing the script they are processed in another batch, but can be done either way.

The part that "parses" ls is the one that does work, the process taht generates the "job" files and the path were it creates them have no spaces. The sendEmail part is the one not working. Every .job file contains the full command (except sendEmail) with all parameters to send the mail, but I can't seem to put it the right way to the program.

---

### Post by HereSomeHow on 2011-09-19
After reading the link above, I finally got it working, what I suspect was wrong, was that 

```
sendEmail $trabajo 
```

sent the whole command line as a single parameter to sendEmail. The solution was:

```
bash -c "sendEmail $trabajo"
```

and voilá!

---

