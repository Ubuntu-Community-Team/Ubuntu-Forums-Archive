---
title: "How to parse a file mode from a shell script"
date: 2011-07-02
forum: General Help
---

### Post by buchs on 2011-07-02
Problem: Sometimes the bash file mode (read/write/execute) tests are not consistent with the actual mode settings, most specifically when one is using sudo. For example, a file may be read-only for the owner and the owner is root, but the effective file permissions when using sudo are wide open, because root can do WHATEVER. This led to a problem for me in one case where I edited /etc/sudoers by changing the mode and then was stuck. I want to detect other situations which would be similar - where a file is read-only for the owner, root, which indicate the intentions of the OS.

Not having found a shell script on the web that would parse the mode characters output by **ls -l** I decided to write one. I am posting it here, so it is available to others and can get indexed. I implemented the main code as a function that runs in Bourne shell and bash. Here is that code:

```
parse_file_mode () {
   indchars=`ls -l $1|sed -e 's/ .*$//' -e 's/\([-rwxse]\)/\1 /g'`
   saveIFS=$IFS
   IFS=" "
   cnt=1
   for ch in $indchars
   do
     case $cnt in
       1) outstr="ftype=$ch" ;;
       2) outstr="$outstr;fownerread=$ch" ;;
       3) outstr="$outstr;fownerwrit=$ch" ;;
       4) outstr="$outstr;fownerexec=$ch" ;;
       5) outstr="$outstr;fgroupread=$ch" ;;
       6) outstr="$outstr;fgroupwrit=$ch" ;;
       7) outstr="$outstr;fgroupexec=$ch" ;;
       8) outstr="$outstr;fotherread=$ch" ;;
       9) outstr="$outstr;fotherwrit=$ch" ;;
       10) outstr="$outstr;fotherexec=$ch" ;;
     esac
     cnt=`expr $cnt + 1`
   done
   IFS=$saveIFS
   echo $outstr
}
```

This will return a string which can be used to set a series of shell variables to indicate the mode characters. It is then possible to use this function with eval, like this:

```
eval `parse_file_mode /etc/sudoers`

```

which will set the variables at the current shell. Thus it could be used in another shell script and the variables will be defined in the current scope. 

I marked this as solved from the start, but comments and improvements are certainly welcome. If anyone also has a better place (forum, repository) to post this, feel free to share it.

---

