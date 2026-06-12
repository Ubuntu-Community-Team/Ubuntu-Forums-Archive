---
title: "help with conky"
date: 2010-10-02
forum: General Help
---

### Post by matt.rebo. on 2010-10-02
im currently using a bash script which has color variables

```
red='\E[31;40m'
green='\E[32;40m'
white='\E[37;40m'
```and im executing the script in conky using

```
${execi 60 ~/scripts/concept.sh}
```im new to conky and researched that it uses hex variables like red (#FF0000), so conky is not recognising the color code and prints it, like 

```
[E31;40m
```is there a way to enable conky to intepret the bash color codes as a hex color? TIA

---

### Post by matt.rebo. on 2010-10-02
a huge thanks to pavelo at irc://irc.freenode.net/conky for solving this!  

in the script i was using the command   

```
echo -en $red  
```

this is because to execute the script in a terminal it requires this format to change the output text to red. i was advised to make the script work when it was being called in conky to amend it to  

```
echo '${color red}'
``` 

and amend the conky command from execi to execpi  

```
${execpi 60 ~/scripts/concept.sh}  
```

it now works perfectly in conky; printing the text output in red! :guitar:

---

