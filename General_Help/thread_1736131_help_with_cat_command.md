---
title: "help with cat command?"
date: 2011-04-22
forum: General Help
---

### Post by ClientAlive on 2011-04-22
Hi,

I'm working through a book to help me learn command line. I came to a part of it that I had difficulty working through the exercise and was hoping someone could help.

The best way I could figure out to do this was make an open office document with the relevant parts of the book pasted in and my comments in line with it. I've attached that document below.

Any help would sure be appreciated as I would like to work this exercise successfully before moving on. This exercise is connected to what we are about to do in the boo.

Thanks in advance for your help.

---

### Post by Ad@m on 2011-04-22
open your terminal and type,

```
cat > file.txt
```Now type,

```
This is a test
```Then press

```
ctrl-d
```then type

```
cat file.txt
```What does your terminal output? 

It should output "This is a test"

---

### Post by ClientAlive on 2011-04-22
```
jake@kLY3ntAlyVe:~$ cat > file.txtthis is a testcat file.txt
cat: is: No such file or directory
cat: a: No such file or directory
cat: testcat: No such file or directory
cat: file.txt: No such file or directory
jake@kLY3ntAlyVe:~$
```

ctrl+d was pressed after "this is a test" and enter after "cat file.txt".

In my previous attempt there was a space between "cat > file.txt" (or what I had chosen to name my file) and the text I wanted to have display. When I did this right now I thought maybe that was where I went wrong.

---------------------------------------

Tried it again with a space in between but when I hit ctrl+d there is no new line given by which I would proceed to enter the next command: "cat file.txt" in order to see the result displayed. When I got no response I hit enter, got a new line and typed the next comand: "cat file.txt". What follows shows the result and a second attempt after that.

In the first code I pasted I just continued to try and enter the second command even though ctrl+d gave no response. I hit enter after that.

```
jake@kLY3ntAlyVe:~$ ls
Appearanc Files  Documents  file.txtthis  Pictures       Ubuntu One
cliPlayground    Downloads  Mozilla       Special Files  Videos
Desktop          eBooks     Music         Templates
jake@kLY3ntAlyVe:~$ rm file.txtthis
jake@kLY3ntAlyVe:~$ ls
Appearanc Files  Documents  Mozilla   Special Files  Videos
cliPlayground    Downloads  Music     Templates
Desktop          eBooks     Pictures  Ubuntu One
jake@kLY3ntAlyVe:~$ cat > file.txt this is a test
cat: this: No such file or directory
cat: is: No such file or directory
cat: a: No such file or directory
cat: test: No such file or directory
jake@kLY3ntAlyVe:~$ ls
Appearanc Files  Documents  file.txt  Pictures       Ubuntu One
cliPlayground    Downloads  Mozilla   Special Files  Videos
Desktop          eBooks     Music     Templates
```

---

### Post by cipherboy_loc on 2011-04-22
For the first part:

```

cipherboy@omniforce-master0:~$ cat
This is a test
This is a test
Press Enter and then Ctrl+D to end
Press Enter and then Ctrl+D to end

```

I entered cat, hit enter, typed in "This is a test", pressed enter, entered "Press Enter and then Ctrl+D to end", pressed enter, and then hit Ctrl+D.

For the second part:
```

cipherboy@omniforce-master0:~$ cat > tmp.txt
This is a test.
Press Enter and then Ctrl+D to end.
As you can see, the text does not repeat. 
That is because it gets redirected to tmp.txt by Bash.
Enter
Ctrl+D
[CODE]

[CODE]
cipherboy@omniforce-master0:~$ cat tmp.txt
This is a test.
Press Enter and then Ctrl+D to end.
As you can see, the text does not repeat.
That is because it gets redirected to tmp.txt by Bash.
Enter
Ctrl+D

```

The new lines are where you hit enter.




Cipherboy

---

### Post by Ad@m on 2011-04-22
As cipherboy_loc pointed out, you have to press the "enter" key after each new line :)

---

### Post by ClientAlive on 2011-04-22
Maybe I mistook what was supposed to be accomplished. I thought there was going to be a file created where it stored that text and that something I did in the exercise was going to display that onto the screen from the file. Maybe it does and you just have to take it on faith. I don't know if it is actually saved into the file but I thought that to check it I could go in and "less" the file and see the text directly from the file - to prove it to myself.

If this is all it is then I guess I'm doing fine - cause' that's what I get too. The other thing is this seemed like a way someone could actually put content into a text file through the terminal. But if it is not saved what would be the use?
------------------------------------------------

> **cipherboy_loc said:**
> For the first part:

```

cipherboy@omniforce-master0:~$ cat
This is a test
This is a test
Press Enter and then Ctrl+D to end
Press Enter and then Ctrl+D to end

```

I entered cat, hit enter, typed in "This is a test", pressed enter, entered "Press Enter and then Ctrl+D to end", pressed enter, and then hit Ctrl+D.

For the second part:
```

cipherboy@omniforce-master0:~$ cat > tmp.txt
This is a test.
Press Enter and then Ctrl+D to end.
As you can see, the text does not repeat. 
That is because it gets redirected to tmp.txt by Bash.
Enter
Ctrl+D
[CODE]

[CODE]
cipherboy@omniforce-master0:~$ cat tmp.txt
This is a test.
Press Enter and then Ctrl+D to end.
As you can see, the text does not repeat.
That is because it gets redirected to tmp.txt by Bash.
Enter
Ctrl+D

```

The new lines are where you hit enter.




Cipherboy


My text has never repeated. That's where I think I'm making some mistake. I'm trying it again right now.

---

### Post by ClientAlive on 2011-04-22
I got it. Thanks cypherboy0.

```
this is a test
this is another test
tmp.txt (END)
```

That's the text from my file and it is being looked at by using "less" to open the actual file. I guess it does save it.

Guess I was just not going about it the right way. Now on to "sort", "uniq", "grep", "wc", and some other stuff for me in this book.

Thanks again guys

Jake

---

### Post by WorMzy on 2011-04-22
"cat" is used to concatenate two files into one, but is (perhaps more commonly) also used to display the contents of a single file. There is very little point in using cat to create a file from nothing, especially since there are text editors like vim, nano, and emacs available which are designed for doing that. It's easier to redirect output from echo if you want to create file on the fly.

e.g.
```
echo "this is a test" > file1.txt
```
```
echo "this is another test" > file2.txt
```

You can then use cat to join the files together:

```
cat file1.txt file2.txt > file3.txt
```

Then display the content of the final file with:

```
cat file3.txt
```

Then edit the content of the file with

```
nano file3
```

(Press Ctrl+X to exit nano)

Hopefully this helps you understand.



Just to clarify: there's nothing wrong with using cat to create files in the way you were suggesting, it's just not common practice (at least as far as I've seen).

---

### Post by ClientAlive on 2011-04-22
> **WorMzy said:**
> "cat" is used to concatenate two files into one, but is (perhaps more commonly) also used to display the contents of a single file. There is very little point in using cat to create a file from nothing, especially since there are text editors like vim, nano, and emacs available which are designed for doing that. It's easier to redirect output from echo if you want to create file on the fly.

e.g.
```
echo "this is a test" > file1.txt
```
```
echo "this is another test" > file2.txt
```

You can then use cat to join the files together:

```
cat file1.txt file2.txt > file3.txt
```

Then display the content of the final file with:

```
cat file3.txt
```

Then edit the content of the file with

```
nano file3
```

(Press Ctrl+X to exit nano)

Hopefully this helps you understand.



Just to clarify: there's nothing wrong with using cat to create files in the way you were suggesting, it's just not common practice (at least as far as I've seen).

Yes. Thank you. The author gave an example similar to that where he was using "cat" to combine files. In his example he was using it to combine multimedia files (mpeg I think) and he used the wildcard "*" to include all files. He said that because the way that wildcard works it would combine the files in the right order.

I kinda figured there are better ways to create a file through the terminal. I was just trying to follow along with the book and taking some guesses about what I could do with "cat".

Thanks so much for the info. I'll keep my eye out for that one too. I'm sure it will come up in what I'm reading and I'll probably try those things out on my own too. Pretty cool!

Jake

---

### Post by WorMzy on 2011-04-22
I wouldn't recommend concatenating multimedia files using cat, even if the produced file is usable, the metadata will be messed up. Just a heads up. :)

---

