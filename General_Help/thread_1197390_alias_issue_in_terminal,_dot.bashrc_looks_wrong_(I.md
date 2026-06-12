---
title: "alias issue in terminal, dot.bashrc looks wrong (I think)"
date: 2009-06-26
forum: General Help
---

### Post by Lostin60's on 2009-06-26
I have a small dilemma.  I just installed Jaunty, and I was going to try to create some aliases in the terminal. (I type sloooow).  I knew it could be done, but wasn't sure how.  So I googled, and found almost what I was looking for.
This is quoted from a forums post

First of all open a terminal and type
```
gedit .bashrc
```
near the end of the file uncomment and change these lines:
```
# Define your own aliases here ...
#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
to:

```
# Define your own aliases here ...
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

All very nice and straight forward. Unfortunately it doesn't exist in quite that way on my computer. All the "do this to" lines are there but the "to's" are non-existant.  The following is from my computer in "/usr/share/base-files/dot.bashrc"

```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See "/usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi
```
and farther down in the file is this

```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi
```

You can see that the only real differences are in the file names and locations.  So, in my system, I went looking, assuming that it would simply be a matter of file name substitution.

Starting from "#Alias Definitions"
I have no ".bash_aliases" file in my system, so I went looking for "examples" in "/usr/share/doc/bash-doc/".  No "examples" there, (which makes sense, since I also don't have the "bash-doc" folder), only "example-content" which contained only a "changelog.gz" and a "copyright" file.  

I have "bash" and "Bash-completion" but they are in "/usr/share/doc".  And as I said I have my "dot.bashrc" file in "usr/share/base-files" folder.


Getting to the next comparable section in the "dot.bashrc" file.
I have "/etc/bash_completion.d" which has 4 unrelated files, and I have  "/etc/profile.d" which contains "gvfs-bash-completion.sh" which seems to deal with how "bash" handels colons and maybe wordbreaks at the end of a line? It reads as follows

```
# Check for bash                                                                
[ -z "$BASH_VERSION" ] && return

####################################################################################################


__gvfs_multiple_uris() {
    local IFS=$'\n'
    local cur="${COMP_WORDS[COMP_CWORD]}"

    COMPREPLY=($(compgen -W '$(gvfs-ls --show-completions "$cur")' -- ""))

    # don't misbehave on colons; See item E13 at http://tiswww.case.edu/php/chet/bash/FAQ
    # We handle this locally be extracting any BLAH: prefix and removing it from the result.
    # Not great, but better than globally changing COMP_WORDBREAKS
    
    case "$cur" in
	*:*)
	    case "$COMP_WORDBREAKS" in
		*:*) colon_prefix=$(echo $cur | sed 's/:[^:]*$/:/' )
		    COMPREPLY=${COMPREPLY##${colon_prefix}}
		    ;;
	    esac
	    ;;
    esac
}

####################################################################################################

complete -o nospace -F __gvfs_multiple_uris gvfs-ls
complete -o nospace -F __gvfs_multiple_uris gvfs-info
complete -o nospace -F __gvfs_multiple_uris gvfs-cat
complete -o nospace -F __gvfs_multiple_uris gvfs-less
complete -o nospace -F __gvfs_multiple_uris gvfs-copy
complete -o nospace -F __gvfs_multiple_uris gvfs-mkdir
complete -o nospace -F __gvfs_multiple_uris gvfs-monitor-dir
complete -o nospace -F __gvfs_multiple_uris gvfs-monitor-file
complete -o nospace -F __gvfs_multiple_uris gvfs-move
complete -o nospace -F __gvfs_multiple_uris gvfs-open
complete -o nospace -F __gvfs_multiple_uris gvfs-rm
complete -o nospace -F __gvfs_multiple_uris gvfs-save
complete -o nospace -F __gvfs_multiple_uris gvfs-trash
complete -o nospace -F __gvfs_multiple_uris gvfs-tree

```

I know that some files changed names in Jaunty, while keeping the same content ie. "/etc/modprobe.d/blacklist" changed to "/etc/modprobe.d/blacklist.conf"  So I figured that might be the issue here, but it doesn't seem to be.  Can't find any files that seem to correlate.

I can't figure out how .bashrc even functions with the commands pointing to non-existant files. I also tried just uncommenting the alias lines in the "dot.bashrc" file, but that didn't work either.

Now I know I am new to this, and I may just be making ignorant mistakes (it wouldn't be the first time), but it seems to me that if the command lines in part of a program  are pointing to non-existant files and folders something isn't right.

Sorry about the way this post looks, but I tried my best to deal with each line of code, in the order they are in in the "dot.bashrc" file, to make it easier to understand.  

So, any and all suggestions and advice will be greatly appreciated.

Remember I mentioned ignorance on my part? It was. It was one of those forest for the trees things.  I am so used to only looking for _folders_ hidden in /home/daniel that I didn't even look beyond the folders to see the _file_ named .bashrc.  Well.....DUH! The heck or it is, I found a way to make it work using the dot.bashrc file.  But it was a good learning exercise for me. From that one small mistake, I gained a lot of insight on how things are coded, both in practice and in theory.  One of these days I might even be the answerer in here instead of being the questioner.

---

### Post by x22 on 2009-08-15
not sure whether you solved the problem.  Usual method
1. put global aliases in /etc/bashrc--everybody gets these
2. put personal aliases--including overrides--in /home/.bashrc
need to be root for 1.

---

### Post by Johnny B on 2009-08-16
> put personal aliases--including overrides--in /home/.bashrc

you should definitely use /home/"yourname"/.bashrc 

this is optional:
> # Define your own aliases here ...
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
if you're using this you need to create the file ~/.bash_aliases
( this symbol ~ means in your home directoy )
its optional because you can put your aliases directly in .bashrc,
.bash_aliases is just in a seperate file to keep your aliases organised, its really only nessacery if you have alot of aliases. i only have 2 or 3, so i put them all the way at the bottom of .bashrc

---

