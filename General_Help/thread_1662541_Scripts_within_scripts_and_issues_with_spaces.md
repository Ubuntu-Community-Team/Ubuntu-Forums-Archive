---
title: "Scripts within scripts and issues with spaces"
date: 2011-01-08
forum: General Help
---

### Post by frankerooney on 2011-01-08
Hi All,
  Just a question re scripting.
I've got a bash script which needs to call another bash script. The second script has an unknown number of arguments (I read these in or generate them in the first script) and they need to have spaces in.
I can't change script2 and it's too big to build the functions it does into script1

so for example

**script1**
#...do stuff
# call script2 with arguments
script2 "argument 1 with spaces" "argument 2 with spaces" ...
# do more stuff

This works fine if arguments explicitly have quotes around, the problem is I don't know how many arguments are passed so I currently do this instead: (some pseudo code in here)

**script1**
#..do stuff
# bit of code done to load args into array called args
# now create string to call from script2 execution below
for (( i = 1;  i<number_of_arguments; i ++ ;))
  do
    argument_string=$argument_string \"{args[$i]}\"
  done
#argument string now contains "argument 1 with spaces" "argument 2 with spaces" etc, including the quotes
# call script2 with arguments by using a string appended on the end
script2 $argument_string
# do more stuff..

Problem is script2 now sees it's arguments not as
argument 1 with spaces
argument 2 with spaces

but
argument
1
with
spaces
argument
2
with
spaces

Am I doing this all wrong, has anyone any ideas?!
I am tearing my hear out!
Thanks in advance.

---

### Post by McNils on 2011-01-08
```
#argument string now contains "argument 1 with spaces" "argument 2 with spaces" etc, including the quotes
# call script2 with arguments by using a string appended on the end
script2 $argument_string
# do more stuff..
```

The problen lies in your call to script2 here. You must quote the variable to keep the data with spaces as one argument, like this

```
script2 "$argumet_string"
```

otherwise you make a call with many arguments like you show.

---

### Post by frankerooney on 2011-01-08
Hi. Thanks for your reply.

I did try that initially and it means the script 2 gets called like this

script2 "argument 1 argument 2"

script2 obviously didn't like it!

Any other ideas?

Thanks
Andy

---

### Post by sisco311 on 2011-01-08
I'm not sure if I understand you example correctly, but I think you want something like:
```
#!/usr/bin/env bash

# script1
script2 "arg 1" "arg 2" "arg 3"

```

```
#!/usr/bin/env bash

# script2
for arg in "$@"; do
  echo "$arg"
done

```

---

### Post by frankerooney on 2011-01-08
Hi sisco311
  Yes, that's what I want to do, but I can't do the line in script1 that says

script2 "arg 1" "arg 2" "arg 3"

because I don't know how many there are, so I've been adding them up in a string variable so variable is "arg 1" "arg 2" "arg 3", then calling

script2 $variable

but it doesn't work with spaces!

I'm stuck!

---

### Post by sisco311 on 2011-01-08
Use an array in script1:
```
arr=( "a 1" "a 2" "b 1" "b 2" )
script2 "${arr[@]}"
```

---

### Post by frankerooney on 2011-01-08
sisco311,
  You've made my day, that works great!

Substitutions weren't working bit by bit, but displaying all variables in the array worked a treat.

Cheers
Andy

---

