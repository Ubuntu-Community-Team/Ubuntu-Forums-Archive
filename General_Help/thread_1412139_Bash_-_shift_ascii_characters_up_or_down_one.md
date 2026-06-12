---
title: "Bash - shift ascii characters up or down one"
date: 2010-02-20
forum: General Help
---

### Post by d3v1150m471c on 2010-02-20
Say you wanted to write a bash script for "hello world" but the characters were shifted up or down by one. How would one go about this?

Example:

```

fdip!#ifmmp!xpsme#

```instead of...
```

echo "hello world"

```

---

### Post by BenAshton24 on 2010-02-20
Is this what you mean?
```
#!/bin/bash
text="Hello World"
aray=( A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z " " " ")
for i in $(seq 0 $((${#text} - 1))); do
	for t in $(seq 0 ${#aray[@]}); do
		if  [[ \"${aray[t]}\" = \"${text:$i:1}\" ]]; then
			str=$str"${aray[t+1]}"
		fi
	done
done
echo $str
```

Output
```
Ifmmp Xpsme
```

Another example, "The quick brown fox jumped over the lazy dog":
```
Uif rvjdl cspxo gpy kvnqfe pwfs uif mbz z eph

```

You can modify the array to include symbols if you want...

---

### Post by raffaele181188 on 2010-02-20
Hmmm, I think this is not so practical (and doesn't care about ASCII values and symbols since it depends on a user-defined array. Of course, you could repicate ASCII values but I think it's not the case)
I am not aware of shell builtin commands or specific Unix tools... You could try caesar/rot13 but they "shifting" doesn't exactly fits your needs
If you can't write a very very simple C program (~10 lines :D) you may use a combination of bash for and a line written in some intermediate language (like Python or Perl, both of which support **ord()** and **chr()** )

---

### Post by d3v1150m471c on 2010-02-20
That's sorta what i was looking for. Mostly I was interested in making the script extra confusing so at first glance, unless you knew something about code, you cannot read it. For instance, I was looking for a way to tell the shell to read the script with the ascii shifted up or down by one character so that the rest of the script could be written shifted either up or down and executed as normal.

---

### Post by BenAshton24 on 2010-02-20
Ohhh I see what you're looking for :P Sorry, I only used the array because i thought that it might be able to add some more functionality to your program if you were doing some sort of encoding thing...

Well, you could do this...

This is the script that shifts the ascii value of your code. Here I'm using "echo 'hello world'". You could quite easily change it to convert your code from a file but I'll leave that to you.
```
#!/bin/bash
text="echo \"Hello World\""
for i in $(seq 0 $((${#text} - 1))); do
	x=$(printf "%d\n" \'${text:$i:1})
	let "x = $x + 1"
	str=$str$(printf "\x$(printf %x $x)")
done
echo $str
```

The output of the above is:
```
fdip#IfmmpXpsme#
```

Now, here is the script that would actually run your code. The variable "text" contains the shifted characters, the script takes these characters, converts them back to how they should be and then pipes them to sh so that the code is executed...
```
#!/bin/bash
text="fdip#IfmmpXpsme#"
for i in $(seq 0 $((${#text} - 1))); do
	if [[ \"${text:$i:1}\" = \"\" ]]; then
		str=$str" "
	else
		x=$(printf "%d\n" \'${text:$i:1})
		let "x = $x - 1"
		str=$str$(printf "\x$(printf %x $x)")
	fi
done
echo $str |sh
```

Output:
```
Hello World
```


Hope this helps you :)

EDIT: Out of curiosity, what exactly are you trying to achieve by disguising your code?

---

### Post by d3v1150m471c on 2010-02-21
> **BenAshton24 said:**
> 
EDIT: Out of curiosity, what exactly are you trying to achieve by disguising your code?

I was working on something that I'd like to be able to share but would only be legible if they knew to reverse shift the code. Nothing malicious, mind you.

---

