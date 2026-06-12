---
title: "Bash programming in the bash shell??"
date: 2009-12-10
forum: General Help
---

### Post by tonyW303 on 2009-12-10
So in gnome-terminal, if I type "set" at the prompt I get something that looks like a library. For example:

user@laptop: set
installed_alternatives () 
{ 
    local admindir;
    for i in alternatives dpkg/alternatives rpm/alternatives;
    do
        [ -d /var/lib/$i ] && admindir=/var/lib/$i && break;
    done;
    for ((i=1; i < COMP_CWORD; i++ ))
    do
        if [[ "${COMP_WORDS[i]}" == --admindir ]]; then
            admindir=${COMP_WORDS[i+1]};
            break;
        fi;
    done;
    COMPREPLY=($( command ls $admindir | grep "^$cur" ))
}
quote () 
{ 
    echo \'${1//\'/\'\\\'\'}\'
}
quote_readline () 
{ 
    local t="${1//\\/\\\\}";
    echo \'${t//\'/\'\\\'\'}\'
}
test () 
{ 
    echo Hello World
}


First off, I don't think this should be happening. Second, I can type the name before the () and it executes. I made test() by just typing "test()" at the prompt. It works but I'm not totally sure what this is. Now to my questions: how do I remove that test() that I created? Also, if this is intended, what is it?
Thanks in advance.

---

### Post by john newbuntu on 2009-12-11
"set" lists all your shell variables and functions.  This is the right behaviour in just about any *nix system.  What you wrote is a function called test.  So, when you type "test" without quotes, it executes the body of that function as expected.
Now, this function is available only for that terminal session. As soon as you exit or close that terminal, it disappears.  Alternatively, you can just say "unset test" and that will remove that function.
For more information, you can type "man bash" on your terminal and read up on the "set" command.

---

