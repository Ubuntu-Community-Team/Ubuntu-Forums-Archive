---
title: "problem with java &amp; azureus"
date: 2006-05-24
forum: General Help
---

### Post by ukasz20 on 2006-05-24
hi

I've managed to install java by make-jpkg mode. downloaded azureus and it is working in windowed mode, but i want to do something else:

this is my goal
[http://azureus.aelitis.com/wiki/index.php/HeadlessSwingUiHowTo](http://azureus.aelitis.com/wiki/index.php/HeadlessSwingUiHowTo)

but when i run 
ukasz@skynet:~/azureus$ java -jar Azureus2.jar --ui=console
Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/cli/CommandLine

please help i really want to run azureus on my server

---

### Post by jvictor on 2006-05-25
get the file from [http://download.nextag.com/apache/jakarta/commons/cli/binaries/cli-1.0.zip](http://download.nextag.com/apache/jakarta/commons/cli/binaries/cli-1.0.zip)

extract the file and 

copy the jar file into the azureus folder taht has other jars 
                                  OR
edit your CLASSPATH and add this jar file to the classpath

HTH

---

### Post by ukasz20 on 2006-05-25
where is that classpath ? and how to add it to classpath ?

i have put that file but still same error

the page says that i have to get Log4j file i have downloaded it but i really don't know how to name it

please help becouse it is worth

---

### Post by jvictor on 2006-05-26
<case-sensitve>CLASSPATH</case-sensitve> is an environment variable that the Java virtual machine(jvm) seaches for to load classes. The problem you are facing is that the JVM is looking for org/apache/commons/cli/CommandLine class but is not able to find it .

So the solution is to add a jar file that contains the needed class into the classpath.
A jar file is v similar to a zip file and contains many classes within it. 

I dont use azureus so i dont know where the jars needed for azureus is stored , so I would suggest to edit a file called .bashrc in ur home directory and add an entry

CLASSPATH=<full_path_name_to_cli.jar>:<full_path_name_to_log4j.jar>:$CLASSPATH
export CLASSPATH

PS
---
an eg will offull_path_name_to_XXXX.jar will be 

/home/xyzuser/jars/log4j.jar


HTH

---

### Post by ukasz20 on 2006-05-29
i have installed azureus and other things like in how to on this forum but azureus won't start in console only :(

---

