---
title: "CaSe changing command?"
date: 2011-09-11
forum: General Help
---

### Post by catlover2 on 2011-09-11
Hello, this may sound odd, but does anyone know of a command that will rename all files and folders in a directory to lower case?

E.g.:

from

/folder/SubfolDEr/Case_SensItive/teXt.txt

to
/folder/subfolder/case_sensitive/text.txt

??

thanks

---

### Post by hakermania on 2011-09-11
Bash scripting! Just made it and it's working fine :)
```

#!/bin/bash
parent_folder="/home/username/parent_folder" #path to the parent folder, EDIT ONLY THIS FROM THE WHOLE SCRIPT
if [ ! -s "$parent_folder" ]; then
 echo "Parent folder does not exist!\n"
 exit 2;
fi
IFS_BAK=$IFS
IFS="
"
for file_or_folder in $(find "$parent_folder"/*); do
    file_or_folder_lowercase=$(echo $file_or_folder | tr '[A-Z]' '[a-z]')
    #sending error messages to null because mv constantly outputs error if filename is same as the destination name
    #as a result, if you have a lowercase name it will not touch it but it will output error
    mv "$file_or_folder" "$file_or_folder_lowercase" 2> /dev/null 
done

IFS=$IFS_BAK

```Although the script is *double* tested I recommend **backing up** your files before executing :)

_*EDIT: this works only if the files have to be renamed(because if folder has been renamed and has subfiles then 'mv' has wrong path.... Working on it*_

---

### Post by jv2112 on 2011-09-11
While that is a nicely built script you could also just use the rename command with the -l option to change to lower case.

---

### Post by hakermania on 2011-09-11
> **jv2112 said:**
> While that is a nicely built script you could also just use the rename command with the -l option to change to lower case.

Argh, don't do this to me :P I just fixed it the other way :P
```

#!/bin/bash
parent_folder="/home/alex/A"
if [ ! -s "$parent_folder" ]; then
 echo "Parent folder does not exist!\n"
 exit 2;
fi
IFS_BAK=$IFS
IFS="
"
#first of all moving all the folders to lowercase
cd "$parent_folder"
for folder in $(find . -depth -type d); do
    folder_lowercase=$(echo $folder | tr '[A-Z]' '[a-z]')
    mv "$folder" "$folder_lowercase" 2> /dev/null
done

#next, move all the files of these folders to lowercase
for file in $(find . -depth); do
    file_lowercase=$(echo $file | tr '[A-Z]' '[a-z]')
    mv "$file" "$file_lowercase" 2> /dev/null
done

IFS=$IFS_BAK

```

---

### Post by gmargo on 2011-09-11
I would add a test to prevent filename collisions (and hence overwrites.)

---

### Post by papibe on 2011-09-11
hakermania's script have problems with some tree structure. For example:
```
$ mkdir -p folder/One/Two/Three

$ ./hakermania.sh

$ find
.
./myfind.sh
./folder
./folder/one
./folder/one/two
./folder/one/two/**Three**
./hakermania.sh
```
I think it has to do with the attempt to rename the whole path:
```
mv: cannot move `./One/Two/Three' to `./one/two/three': No such file or directory
```
I've tested this with several tree structures and files, and it seems to work:
```
$ find . -depth -type d -exec bash -c 'shopt -s dotglob; cd "{}"; rename -v y/A-Z/a-z/ *' \;
```
I set the dotglob option so it can change the hidden files too.

Hope it helps,
Regards.

BTW: the command 'rename' doesn't have an '-l' option.

---

### Post by hakermania on 2011-09-11
The above solution wasn't so good because it renamed the extensions as well, so I found this problem interesting and I spent one hour today to make this program in C++ that renames Upper to Lower and vice versa with both GUI interface and CLI. It renames recursively the filenames by specifying the folder and works with english characters only:
Command line usage:
```

alex@MaD-pc:~/Qt/rename$ find /home/alex/Pictures/ -type f
/home/alex/Pictures/dfcv/AD SF.gif
/home/alex/Pictures/dfcv/ADSF.gif
/home/alex/Pictures/ADSF.gif
/home/alex/Pictures/DTMSIG.jpg
/home/alex/Pictures/ADSF.png
/home/alex/Pictures/ISTOCKPHOTO_1032952-LEMON-CARTOON.jpg
/home/alex/Pictures/adsf.gif
/home/alex/Pictures/ADSF-REBOOT-L.jpg
alex@MaD-pc:~/Qt/rename$ ./rename utl ~/Pictures
Renaming /home/alex/Pictures/ADSF.gif to /home/alex/Pictures/adsf.gif skipped because the latter exists!
alex@MaD-pc:~/Qt/rename$ find /home/alex/Pictures/ -type f
/home/alex/Pictures/dfcv/ad sf.gif
/home/alex/Pictures/dfcv/adsf.gif
/home/alex/Pictures/ADSF.gif
/home/alex/Pictures/dtmsig.jpg
/home/alex/Pictures/istockphoto_1032952-lemon-cartoon.jpg
/home/alex/Pictures/adsf.png
/home/alex/Pictures/adsf.gif
/home/alex/Pictures/adsf-reboot-l.jpg

```So, mainly "rename utl/ltu /path/to/folder" where utl=Upper to Lower and ltu vice versa.
Notice the warning that the file already exists? Thanks gmargo!

It also has a GUI interface which launches when no arguments are specified (for the CLI haters or newbies):
[IMG]http://i.imgur.com/a3i4P.png[/IMG]

On the end of the post there's the source and the executable compiled for i386(32 bit) if anybody interested.

To run, please run first this to install the libraries the program need:
```

sudo apt-get install libqtgui4 qtcore4

```If you want to compile from source (example you have 64 bit) you will also need
```

sudo apt-get install qt4-qmake

```and building is as easy as:
```

cd /to/source
qmake -project
qmake *.pro
qmake
make

```i386 Binary: [http://ubuntuone.com/6GCr9WHe3Mm0D17j1LT4IK](http://ubuntuone.com/6GCr9WHe3Mm0D17j1LT4IK)
Source:  [http://ubuntuone.com/4XNejMMGhxMqFB4jxdlnBo](http://ubuntuone.com/4XNejMMGhxMqFB4jxdlnBo)

EDIT: too much noise eh? It doesn't matter, I had fun programming this smally8-)

---

### Post by catlover2 on 2011-09-11
Hello, for some reason I had problems with the original script that hakermania posted, but the second one worked fine. 

I'll open another thread if needed, is it possible with another script, to change all characters within all plain text documents within a directory, limited by file extension,  to lower case?


EDIT i didn't see the above before posting, I'll give it a try if i ever need to do this again.

---

### Post by hakermania on 2011-09-11
> **catlover2 said:**
> Hello, for some reason I had problems with the original script that hakermania posted, but the second one worked fine. 

I'll open another thread if needed, is it possible with another script, to change all characters within all plain text documents within a directory, limited by file extension,  to lower case?


EDIT i didn't see the above before posting, I'll give it a try if i ever need to do this again.

You should be made to post programming challenges, working on it :)

---

### Post by hakermania on 2011-09-11
Dataaa!

There's no time to provide the links but if you want you can compile from here because tomorrow's the 1st day at  school and i have to go to sleep. Similarly as above, ./executable  utl/ltu /path/to/dir and renames recursively the files that 'file' finds  as ascii to lower/upper case
```

#include <QtCore/QCoreApplication>
#include <QFile>
#include <QString>
#include <QDir>
#include <QProcess>
#include <QTextStream>

#include <iostream>
using namespace std;

QStringList rename_ltu(QStringList basename){
    int basename_count=basename.count();
    for(int i=0; i<basename_count; i++){
        QString temp = basename.at(i);
        temp.replace("a", "A");
        temp.replace("b", "B");
        temp.replace("c", "C");
        temp.replace("d", "D");
        temp.replace("e", "E");
        temp.replace("f", "F");
        temp.replace("g", "G");
        temp.replace("h", "H");
        temp.replace("i", "I");
        temp.replace("j", "J");
        temp.replace("k", "K");
        temp.replace("l", "L");
        temp.replace("m", "M");
        temp.replace("n", "N");
        temp.replace("o", "O");
        temp.replace("p", "P");
        temp.replace("q", "Q");
        temp.replace("r", "R");
        temp.replace("s", "S");
        temp.replace("t", "T");
        temp.replace("u", "U");
        temp.replace("v", "V");
        temp.replace("w", "W");
        temp.replace("x", "X");
        temp.replace("y", "Y");
        temp.replace("z", "Z");
        basename.replace(i, temp);
    }
    return basename;
}

QStringList rename_utl(QStringList basename){
    int basename_count=basename.count();
    for(int i=0; i<basename_count; i++){
        QString temp = basename.at(i);
        temp.replace("A", "a");
        temp.replace("B", "b");
        temp.replace("C", "c");
        temp.replace("D", "d");
        temp.replace("E", "e");
        temp.replace("F", "f");
        temp.replace("G", "g");
        temp.replace("H", "h");
        temp.replace("I", "i");
        temp.replace("J", "j");
        temp.replace("K", "k");
        temp.replace("L", "l");
        temp.replace("M", "m");
        temp.replace("N", "n");
        temp.replace("O", "o");
        temp.replace("P", "p");
        temp.replace("Q", "q");
        temp.replace("R", "r");
        temp.replace("S", "s");
        temp.replace("T", "t");
        temp.replace("U", "U");
        temp.replace("V", "v");
        temp.replace("W", "w");
        temp.replace("X", "x");
        temp.replace("Y", "y");
        temp.replace("Z", "z");
        basename.replace(i, temp);
    }
    return basename;
}

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);
    if(a.argc()!=3){
        cerr << "2 arguments needed\n";
        return 2;
    }
    QString first(argv[1]);
    if(first!="utl" && first!="ltu"){
        cerr << "1st argument must be either utl or ltu\n";
        return 2;
    }
    QString folder(argv[2]);
    folder.replace("~", QDir::homePath());
    if(!QFile(folder).exists()){
        cerr << QString("Folder "+folder+" does not exist!").toLocal8Bit().data();
        return 2;
    }
    QProcess *list_files = new QProcess(0);
    QStringList args;
    args << folder << "-type" << "f";
    list_files->start(QString("find"), args);
    list_files->waitForFinished(100000);
    QByteArray data = list_files->readAllStandardOutput();
    QString text = QString(data).toUtf8();
    QStringList list = text.split('\n');
    int list_count=list.count()-1; //<- the -1 here so as to avoid the last \n
    QProcess *check_if_plain_text = new QProcess(0);
    args.clear();
    args << "-b" << "";
    QString filename="", type="";
    QByteArray data2;
    if(first=="utl"){
        for (int i=0; i<list_count; i++){
            filename=list.at(i);
            args.replace(1, filename);
            check_if_plain_text->start("file", args);
            check_if_plain_text->waitForFinished(1000);
            data2=check_if_plain_text->readAllStandardOutput();
            type=QString(data2);
            if(type!="ASCII text\n"){
                cerr << QString("Skipping file " + filename + " because it's not ascii text!\n").toLocal8Bit().data();
                continue;
            }
            else
            {
                QFile file(filename);
                QStringList lines;
                file.open(QIODevice::ReadOnly);
                QTextStream readData(&file);
                while (!readData.atEnd())
                    lines << readData.readLine();
                file.close();
                QStringList lines_final=rename_utl(lines);
                int lines_count=lines_final.count();
                file.open(QIODevice::WriteOnly);
                QTextStream writeData(&file);
                for (int i=0; i<lines_count; i++)
                    writeData << lines_final.at(i) << endl;
                file.close();
            }
        }
        return 0;
    }
    else if(first=="ltu"){
        for (int i=0; i<list_count; i++){
            filename=list.at(i);
            args.replace(1, filename);
            check_if_plain_text->start("file", args);
            check_if_plain_text->waitForFinished(1000);
            data2=check_if_plain_text->readAllStandardOutput();
            type=QString(data2);
            if(type!="ASCII text\n"){
                cerr << QString("Skipping file " + filename + " because it's not ascii text!\n").toLocal8Bit().data();
                continue;
            }
            else
            {
                QFile file(filename);
                QStringList lines;
                file.open(QIODevice::ReadOnly);
                QTextStream readData(&file);
                while (!readData.atEnd())
                    lines << readData.readLine();
                file.close();
                QStringList lines_final=rename_ltu(lines);
                int lines_count=lines_final.count();
                file.open(QIODevice::WriteOnly);
                QTextStream writeData(&file);
                for (int i=0; i<lines_count; i++)
                    writeData << lines_final.at(i) << endl;
                file.close();
            }
        }
        return 0;
    }
    else
        return 0;
}

```

---

### Post by sisco311 on 2011-09-11
Oh, boy, oh boy... :)

I'd try something like:
```

cd path/to/dir
find ./ -depth -name '*[A-Z]*' -execdir bash -c 'mv -b -- "$1" "${1,,}"' _ '{}' \;

```

---

### Post by papibe on 2011-09-11
Impressive!

I understand now the use of -execdir (if you see my example I used -exec and then I 'cd' to it).

I can't seem to understand the trailing:
```
_ '{}'
```
It may seem that you solved the problem with argument of the bash -c. Would you care to take a look at my solution?

Thanks in advance for any comment.

Regards.

---

### Post by catlover2 on 2011-09-11
> **sisco311 said:**
> Oh, boy, oh boy... :)

I'd try something like:
```

cd path/to/dir
find ./ -depth -name '*[A-Z]*' -execdir bash -c 'mv -b -- "$1" "${1,,}"' _ '{}' \;

```


That looks a bit less intimidating than the source code the last person posted, but how exactly do I use this?

I *only* want to modify the contents of .lst files.

---

### Post by sisco311 on 2011-09-11
> **papibe said:**
> Impressive!

I understand now the use of -execdir (if you see my example I used -exec and then I 'cd' to it).

I can't seem to understand the trailing:
```
_ '{}'
```
It may seem that you solved the problem with argument of the bash -c. Would you care to take a look at my solution?

Thanks in advance for any comment.

Regards.

From: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

*When bash -c executes a command, the next argument after the command is used as $0 (the script's "name" in the process listing), and subsequent arguments become the positional parameters ($1, $2, etc.). This means that the filename passed by find (in place of the {}) becomes the first parameter of the script -- and is referenced by $1 inside the mini-script. (Don't omit the _ and try to use $0 inside the mini-script -- not only would that be more confusing, but it is also prone to failure if the filename provided by find has special meaning as an argument to the shell.)*

Also check out: [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030)

---

### Post by sisco311 on 2011-09-11
> **catlover2 said:**
> That looks a bit less intimidating than the source code the last person posted, but how exactly do I use this?

I *only* want to modify the contents of .lst files.

Well, you cd into the directory where the files are located and run the command. :) Or you could simply replace **./** with the full or relative path to the directory: **find /home/user/my-dir ...**

If you only want to rename .lst files, then instead of the -name test use: **-name '*[A-Z]*.lst'**

```
find /home/user/my-dr -depth -name '*[A-Z]*.lst' -type f -execdir bash -c 'mv -b -- "$1" "${1,,}"' _ '{}' \;
```

NOTE: I added a -type test to only rename files.

---

### Post by catlover2 on 2011-09-11
so, what does this mean? 

```
reed@Reeds-custom-computer:~/Desktop/Ysflight$ find /home/reed/Desktop/Ysflight -depth -iname '*[A-Z]*.lst' -execdir bash -c 'mv -b -- "$1" "${1,,}"' _ '{}' \;
mv: `./aircep.lst' and `./aircep.lst' are the same file
mv: `./scenery.lst' and `./scenery.lst' are the same file
mv: `./ground.lst' and `./ground.lst' are the same file
mv: `./aircraft.lst' and `./aircraft.lst' are the same file
mv: `./sce_raceway_mh3w.lst' and `./sce_raceway_mh3w.lst' are the same file
mv: `./sce_raceway_mh3w.lst' and `./sce_raceway_mh3w.lst' are the same file
mv: `./ground_mh3wextra.lst' and `./ground_mh3wextra.lst' are the same file
mv: `./ground_mh3wextra.lst' and `./ground_mh3wextra.lst' are the same file
mv: `./ground_cvn241.lst' and `./ground_cvn241.lst' are the same file
mv: `./gro_stunts.lst' and `./gro_stunts.lst' are the same file
mv: `./ground_cvn241.lst' and `./ground_cvn241.lst' are the same file
mv: `./gro_stunts.lst' and `./gro_stunts.lst' are the same file
mv: `./airkzsafull.lst' and `./airkzsafull.lst' are the same file
mv: `./airkzsafull.lst' and `./airkzsafull.lst' are the same file
mv: `./aircep.lst' and `./aircep.lst' are the same file
mv: `./aircep.lst' and `./aircep.lst' are the same file
mv: `./scenary.lst' and `./scenary.lst' are the same file
mv: `./scenary.lst' and `./scenary.lst' are the same file
mv: `./airrc.lst' and `./airrc.lst' are the same file
mv: `./airysfasfx.lst' and `./airysfasfx.lst' are the same file
mv: `./f86d.lst' and `./f86d.lst' are the same file
mv: `./airf-1a(gran).lst' and `./airf-1a(gran).lst' are the same file
mv: `./airf-1a(gran).lst' and `./airf-1a(gran).lst' are the same file
mv: `./airf15ac.lst' and `./airf15ac.lst' are the same file
mv: `./airf15ac.lst' and `./airf15ac.lst' are the same file
mv: `./f86d.lst' and `./f86d.lst' are the same file
mv: `./airf117.lst' and `./airf117.lst' are the same file
mv: `./airf117.lst' and `./airf117.lst' are the same file
mv: `./ysuninst1378.lst' and `./ysuninst1378.lst' are the same file
mv: `./ysuninst3607.lst' and `./ysuninst3607.lst' are the same file
mv: `./sce_rocketsport.lst' and `./sce_rocketsport.lst' are the same file
mv: `./scenery.lst' and `./scenery.lst' are the same file
mv: `./scesjapan.lst' and `./scesjapan.lst' are the same file
mv: `./scenerytf58.lst' and `./scenerytf58.lst' are the same file
mv: `./scebuta.lst' and `./scebuta.lst' are the same file
mv: `./scecircuit.lst' and `./scecircuit.lst' are the same file
mv: `./scekzs.lst' and `./scekzs.lst' are the same file
mv: `./sce_mh3w.lst' and `./sce_mh3w.lst' are the same file
mv: `./grobuta.lst' and `./grobuta.lst' are the same file
mv: `./gro_mh3w.lst' and `./gro_mh3w.lst' are the same file
mv: `./groundtf58.lst' and `./groundtf58.lst' are the same file
mv: `./grocircuit.lst' and `./grocircuit.lst' are the same file
mv: `./grokzs.lst' and `./grokzs.lst' are the same file
mv: `./gro_rocketsport.lst' and `./gro_rocketsport.lst' are the same file
mv: `./ground.lst' and `./ground.lst' are the same file
mv: `./gro_stunts.lst' and `./gro_stunts.lst' are the same file
mv: `./grosjapan.lst' and `./grosjapan.lst' are the same file
mv: `./aircep.lst' and `./aircep.lst' are the same file
mv: `./air_santas_sleigh.lst' and `./air_santas_sleigh.lst' are the same file
mv: `./airkzsd.lst' and `./airkzsd.lst' are the same file
mv: `./air_mh3w_b.lst' and `./air_mh3w_b.lst' are the same file
mv: `./airysfa.lst' and `./airysfa.lst' are the same file
mv: `./air_rocketsport.lst' and `./air_rocketsport.lst' are the same file
mv: `./air_pimped.lst' and `./air_pimped.lst' are the same file
mv: `./aircraft.lst' and `./aircraft.lst' are the same file
mv: `./air_tf58.lst' and `./air_tf58.lst' are the same file
mv: `./airm_vessels.lst' and `./airm_vessels.lst' are the same file
mv: `./airceplt.lst' and `./airceplt.lst' are the same file
mv: `./airkzsafull.lst' and `./airkzsafull.lst' are the same file
mv: `./airm_toybox.lst' and `./airm_toybox.lst' are the same file
mv: `./airsjapan.lst' and `./airsjapan.lst' are the same file
mv: `./airbuta.lst' and `./airbuta.lst' are the same file
mv: `./aircep2-2.lst' and `./aircep2-2.lst' are the same file
mv: `./aircep2-1.lst' and `./aircep2-1.lst' are the same file
mv: `./air_ipc.lst' and `./air_ipc.lst' are the same file
mv: `./aircircuit.lst' and `./aircircuit.lst' are the same file
mv: `./airm_vehicles.lst' and `./airm_vehicles.lst' are the same file
mv: `./air_mh3w.lst' and `./air_mh3w.lst' are the same file
reed@Reeds-custom-computer:~/Desktop/Ysflight$ 

```

nothing seems to have been modified.

---

### Post by sisco311 on 2011-09-11
It means that I need more coffee. :)

Sorry, I used -iname test insead of -name, which is case insensitive, so the command tries to rename files which don't contain any uppercase letter.

---

### Post by catlover2 on 2011-09-11
If I change -iname to -name, it does and outputs nothing.
Am I missing something?

---

### Post by sisco311 on 2011-09-11
By default the mv command is silent. You can use its -v option to make it verbose: **mv -b -v -- ...**

---

### Post by hakermania on 2011-09-12
> **sisco311 said:**
> Oh, boy, oh boy... :)

I'd try something like:
```

cd path/to/dir
find ./ -depth -name '*[A-Z]*' -execdir bash -c 'mv -b -- "$1" "${1,,}"' _ '{}' \;

```
I have to say that my code is more understandable than this chaos :lolflag:

PS1: It doesn't work for me even with 'name' (oh, I see, it works for renaming Upper to lower, but as I say to PS2 this was solved, thanks for the nice solution though :))
PS2: Does it replace the characters of all files recursively in a directory? The OP solved his initial problem with my 2nd script and now wanted to replace all charactes recursively etc ( see #8 )

EDIT: Usage of my last-posted code:
```

alex@MaD-pc:~/Qt/file_rename$ ls ~/bluetooth
a  b  bgh
alex@MaD-pc:~/Qt/file_rename$ cat ~/bluetooth/*
abcdefghijkasldkfj
adsjfhlasjkfhadljkhjkg
alex@MaD-pc:~/Qt/file_rename$ ./file_rename ltu ~/bluetooth/
Skipping file /home/alex/bluetooth/bgh because it's not ascii text!
alex@MaD-pc:~/Qt/file_rename$ cat ~/bluetooth/*
ABCDEFGHIJKASLDKFJ
ADSJFHLASJKFHADLJKHJKG
alex@MaD-pc:~/Qt/file_rename$ ./file_rename utl ~/bluetooth/
Skipping file /home/alex/bluetooth/bgh because it's not ascii text!
alex@MaD-pc:~/Qt/file_rename$ cat ~/bluetooth/*
abcdefghijkasldkfj
adsjfhlasjkfhadljkhjkg

```So, to the thread starter, you can send all your .lst files to a folder and run as above (if 'file' doesn't identify them as ASCII text then run 'file -b lst_file.lst' to see what it is outputed and replace inside my code the string 'ASCII text' with this output (don't forget to leave the \n that is after the 'ASCII text' as is)

---

### Post by sisco311 on 2011-09-12
> **hakermania said:**
> I have to say that my code is more understandable than this chaos :lolflag:

Let me try explain it. :)

**find ./** searches for files in the directory recursively 

**-depth** means process each directory's content before the directory itself.

**-name '*[A-Z]*'** means search only for files with uppercase characters in their name.

**-execdir command ;** runs the command in the subdirectory containing the matched file. {} is replaced by the current file name being processed. 

**mv -b -- ...** renames the file to lowercase. It creates a backup file if the destination file exists.

Now about your second script... :)

First check out BashPitfalls nr.1 (link in my sig).


In most cases you can use parameter expansion instead of **echo | tr/sed/whatever**. Bash 4 has I nice one for this ${parameter,,} converts each uppercase character to lowercase.

Instead of A-Z (a-z) you should use [:upper:] ([:lower:]) or you should make sure that you are using the C or POSIX locale. I probably should have change the locale too. 

Check out BashFAQ #30 for more details and examples.


> **hakermania said:**
> 
PS1: It doesn't work for me even with 'name' (oh, I see, it works for renaming Upper to lower, but as I say to PS2 this was solved, thanks for the nice solution though :))
PS2: Does it replace the characters of all files recursively in a directory? The OP solved his initial problem with my 2nd script and now wanted to replace all charactes recursively etc ( see #8 )


Oh, I missed the OP's 2nd question, I thought now he wants to rename only the .lst files.

sed or can be used for editing streams and files.

Something like:
```
find ./ -iname '*.lst' -type f -exec sed -i -e 's/\(.*\)/\L\1/' '{}' +
```
should do the trick.

---

### Post by hakermania on 2011-09-12
> **sisco311 said:**
> Let me try explain it. :)

**find ./** searches for files in the directory recursively 

**-depth** means process each directory's content before the directory itself.

**-name '*[A-Z]*'** means search only for files with uppercase characters in their name.

**-execdir command ;** runs the command in the subdirectory containing the matched file. {} is replaced by the current file name being processed. 

**mv -b -- ...** renames the file to lowercase. It creates a backup file if the destination file exists.

Now about your second script... :)

First check out BashPitfalls nr.1 (link in my sig).


In most cases you can use parameter expansion instead of **echo | tr/sed/whatever**. Bash 4 has I nice one for this ${parameter,,} converts each uppercase character to lowercase.

Instead of A-Z (a-z) you should use [:upper:] ([:lower:]) or you should make sure that you are using the C or POSIX locale. I probably should have change the locale too. 

Check out BashFAQ #30 for more details and examples.
Thanks, I've already looked at it (from the same sig :P)
Also, thanks for the explanation about the command, 'find' is power, definitely!

I wanted to re-invent the wheel :guitar:

---

### Post by catlover2 on 2011-09-12
> **sisco311 said:**
> Let me try explain it. :)

**find ./** searches for files in the directory recursively 

**-depth** means process each directory's content before the directory itself.

**-name '*[A-Z]*'** means search only for files with uppercase characters in their name.

**-execdir command ;** runs the command in the subdirectory containing the matched file. {} is replaced by the current file name being processed. 

**mv -b -- ...** renames the file to lowercase. It creates a backup file if the destination file exists.

Now about your second script... :)

First check out BashPitfalls nr.1 (link in my sig).


In most cases you can use parameter expansion instead of **echo | tr/sed/whatever**. Bash 4 has I nice one for this ${parameter,,} converts each uppercase character to lowercase.

Instead of A-Z (a-z) you should use [:upper:] ([:lower:]) or you should make sure that you are using the C or POSIX locale. I probably should have change the locale too. 

Check out BashFAQ #30 for more details and examples.




Oh, I missed the OP's 2nd question, I thought now he wants to rename only the .lst files.

sed or can be used for editing streams and files.

Something like:
```
[COLOR=Red]find ./ -iname '*.lst' -type f -exec sed -i -e 's/\(.*\)/\L\1/' '{}' +[/COLOR]
```should do the trick.

I still have no idea how it worked, but it worked!:)

Thanks alot!

---

