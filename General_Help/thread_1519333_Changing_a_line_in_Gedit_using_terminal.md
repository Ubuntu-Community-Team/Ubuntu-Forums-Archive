---
title: "Changing a line in Gedit using terminal?"
date: 2010-06-28
forum: General Help
---

### Post by pepsifx357 on 2010-06-28
I have a .sh file that I need to change one line every time I execute it.  Right now I keep having to open up the file and change the line to use it.

How can I create a .sh file that creates a random name whenever it's executed.

Here is the line:

```
cattach /home/user/.tag mock
```

I need to change the word "mock" every time I execute the .sh file. How could I do that?

Then on the other .sh that I have, this word "mock" also needs to be changed, but it needs to mirror the random name given in the first .sh file.

Any help with this would be much appreciated.

Ben

---

### Post by gadolinio on 2010-06-28
> **pepsifx357 said:**
> I have a .sh file that I need to change one line every time I execute it.  Right now I keep having to open up the file and change the line to use it.

How can I create a .sh file that creates a random name whenever it's executed.

Here is the line:

```
cattach /home/user/.tag mock
```I need to change the word "mock" every time I execute the .sh file. How could I do that?

Then on the other .sh that I have, this word "mock" also needs to be changed, but it needs to mirror the random name given in the first .sh file.

Any help with this would be much appreciated.

Ben

Aaahhh... interesting thing. Unfortunately i can only give you some tool you can try:

```

sed -i 's/text_you_have_now/text_you_want/g' your_script.sh

```

So you can create the 2ndScript, which has the sed command with the word you have, and the word you want to replace it with.

Now, how would you tell the 2ndScript which is the present word? Mmmmm I can only think of having the command alone in a text file, and use the AWK command to print the third column ("cattach" is the first,  "/home/user/.tag" is the second, and"mock" is the third; spaces separate columns). Do some web search for more detailed instructions... I can't remember more. Here's one I've used, but can't remember how I built it:
```
awk '/:/ {print $1}' text_file's_name
```

Well, back to where we were: maybe you could set a variable to be the result of awk, and then use that variable as the present word in the sed command. 

And how would you create random names? I have no idea.

Hope this hints help you!

---

### Post by pepsifx357 on 2010-06-28
I appreciate the effort! 

I just realized that there would have to be a program designed to give random "names" for this to work.  Otherwise it would need me to specify the names to be given.

I'm using cfs to encrypt files and I'm using .sh files to enact the decrypting and encrypting, using launchers to make it quicker.

The first decrypt.sh has these lines:

```
cattach /home/user/.tag mock
```

```
nautilus /crypt
```

"mock" being the folder that is attached to the encrypted folder under /crypt

The second .sh files has this line:

```
cdetach mock
```

Now it will remove the "mock" folder.

When the folder is attached in the first .sh file, I want it to be a random name everytime.  And for the second .sh to work, it would need to know the random name given to the first .sh

---

### Post by gadolinio on 2010-06-28
If you use the command in a different file, the main script should call it with
```
`cat file's_name`
```That piece, in the script, would act as the text contained in the file would do.
This is only because I can't think of another way of pointing to the <present word> other than awk, and it counts columns in a whole file, so the entire content of the file will be searched for the column you specify.

So your main script would be, in the first place:
```

blah blah blah, script....
cattach /home/user/.tag mock
blah blah blah, more script....

```That could be changed to
```

blah blah blah, script....
`cat name_of_the_file_with_your_command`
blah blah blah, more script....

```The file would be, of course, plain text containing only this line
```

cattach /home/user/.tag mock

```And then the second script should point to that file, look for the word "mock" (with awk or whichever tool you want), print that so that the output is used by sed to know what to replace. And then comes the issue of the random name.

You could also do it slightly different: if you can create the random word so that it always begins with "cattach /home/user/.tag ", the random part would be added. I mean, random words have to be "cattach /home/user/.tag hello", "cattach /home/user/.tag byebye", "cattach /home/user/.tag whatever", etc. Then, you just use the cat command to make that string the entire and only new content of the text file that in the beginning has "cattach /home/user/.tag mock".

Well, hope you find this useful. Or at least that you've understood what I'm trying to say... I'm not sure I do myself :S

Good luck!


EDIT: there was no reason for including "cattach /home/user/.tag" before "mock" in the separate file, as the first part is always the same. I really need some sleep XD

---

### Post by gadolinio on 2010-06-28
> **pepsifx357 said:**
> 
And for the second .sh to work, it would need to know the random name given to the first .sh

I see. Well, the random word creator is another part of the problem. Let's first think how to do the rest. You could just write both scripts, but every time you need the folder's name, you instead write 
```
`cat name_of_the_file_containing_the_folder's_name`
```God bless the quotes ` `   That code will simply be replaced for "mock" or whatever the file's content is at that moment.
Both scripts will point at the same text file, every time they need to use "mock". So even if you use the folder mock more than once in the script, create more scripts, etc, you won't have to change the word each time it appears in each script. The problem is simply (yeah, i know... ) how to create random text strings. Then inserting that into the text file shouldn't be difficult.

---

### Post by DaithiF on 2010-06-28
Hi,
in the first script, pick a random word from a dictionary file, write that word to a file which both your scripts then read & use as a parameter to your cattach / cdetach commands.

So your first script would contain (for example):
```
sed -n "${RANDOM}p" /usr/share/dictionary/words | tr -d "'" > ~/.currentword
tag=$(cat ~/.currentword)
cattach /home/user/.tag $tag

```

and the second script:
```
tag=$(cat ~/.currentword)
cdetach $tag

```

---

### Post by pepsifx357 on 2010-06-28
Ok, I'm still new to scripting so I might be a little slow at this.  How would I make this dictionary file?

---

### Post by stderr on 2010-06-28
No need 

```
head -n 5 /usr/share/dict/words

A
A's
AOL
AOL's
```

However, I might be more tempted to use pseudorandom numbers from /dev/urandom and scale them to fall within ASCII character values.

---

### Post by gadolinio on 2010-06-29
> **DaithiF said:**
> Hi,
in the first script, pick a random word from a dictionary file, write that word to a file which both your scripts then read & use as a parameter to your cattach / cdetach commands.

So your first script would contain (for example):
```
sed -n "${RANDOM}p" /usr/share/dictionary/words | tr -d "'" > ~/.currentword
tag=$(cat ~/.currentword)
cattach /home/user/.tag $tag

```and the second script:
```
tag=$(cat ~/.currentword)
cdetach $tag

```

VERY interesting...

---

### Post by DaithiF on 2010-06-29
> **pepsifx357 said:**
>  How would I make this dictionary file?
As stderr's reply suggests, no need to make it, you already have it.

---

### Post by Jakiejake on 2010-06-29
> **pepsifx357 said:**
> I have a .sh file that I need to change one line every time I execute it.  Right now I keep having to open up the file and change the line to use it.

How can I create a .sh file that creates a random name whenever it's executed.

Here is the line:

```
cattach /home/user/.tag mock
```

I need to change the word "mock" every time I execute the .sh file. How could I do that?

Then on the other .sh that I have, this word "mock" also needs to be changed, but it needs to mirror the random name given in the first .sh file.

Any help with this would be much appreciated.

Ben

Was thinking almost the same thing this morning!

---

