---
title: "Positional parameters"
date: 2012-03-29
forum: General Help
---

### Post by al_mic on 2012-03-29
Hello,

I'm not sure that even the title is right, but here I am asking because I want to know.
There is a thing in linux where you can pass the output of a command through a pipe to a second command. And that second command should not take the output as the first parameter, but place it wherever you want.
I read about this some time ago and it may be possible that I'm mixing things, but I know it had something to do whit brackets.

I will try to write an example:

path="/var/www/test/"
echo $path | cp -R /var/www/uploads/* $1

or

echo $path | cp -R /var/www/uploads/* ($1)
 

I know that in a bash script $1 is the first parameter that was used when calling the script, but I do not remember something else about these positional expressions that could take the value of a previous result.

Do you understand what I am talking about?

Thanks.

---

### Post by papibe on 2012-03-29
Hi al_mic.

Pipes don't use parameters. They pass the standard output of a command to standard input of the next one. For the trick to work the second command has to work this way: if called with no parameters, it reads from the standard input.

For example take the command 'sort'. The usual way you call it is:
```
sort file
```
That will read the content of the file, sort it and write the output.

If, instead, you call 'sort' with no parameter, it will start reading from the terminal:
```
$ sort
z 
m
a
^D

a
m
z 

$
```
When a command works like that, it is very easy use it in a pipe. For instance: you want to get a list of your files and directories order by how much size they use.
```
du -s * | sort -n -r
```
No that '-n' and '-r' are not parameters, but options.

If the second command in the pipe does not work with the standard input (like 'cp' for example), you can't use it in a pipe directly. In that case you may need to use 'xargs'.

'xargs', as a good pipe command, reads the standard input. However, it call a another program with what it reads as parameters. For example, let's say that you want to backup/copy all your shell scripts (located in different subdirectories).
```
find -name '*.sh' | xargs cp -vb '{}' /path/to/scripts/backup/dir
```
'{}' represents the list of names find by 'find'.

Note since filenames can contain spaces (or other problematic characters), the safest way to use that structure is separating the file names with a null character:
```
find -name '*.sh' -print0 | xargs -0 cp -vb '{}' /path/to/scripts/backup/dir
```

Does that clarify things a little bit?
Tell us if you need more helps with that.
Regards.

---

