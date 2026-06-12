---
title: "Terminal command"
date: 2011-08-12
forum: General Help
---

### Post by ajits on 2011-08-12
where can I get more terminal command and it use?:D

---

### Post by Nimbus200 on 2011-08-12
$ man <command>
or
$man <tab>
to list all command available for your currently logged in user

---

### Post by SidebySide on 2011-08-12
Precise:
```
 <Command> --help
```Comprehensive:
```
 info <Command>
```-------------------------------------------------------------
[FONT=Times New Roman, serif][SIZE=2][COLOR=#0000ff]_[[COLOR=#0000ff]http://ss64.com/bash[/COLOR]]("http://ss64.com/bash/")_[/COLOR][/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Times New Roman, serif][SIZE=2][COLOR=#0000ff]_[[COLOR=#0000ff]http://www.thegeekstuff.com[/COLOR]]("http://www.thegeekstuff.com/")_[/COLOR][/SIZE][/FONT][SIZE=2]
[/SIZE][http://wiki.ubuntu.ir/BashCommands](http://wiki.ubuntu.ir/BashCommands) (List of commands)
[http://www.jetup.ir/do.php?filename=01_05_1113042581371.gz](http://www.jetup.ir/do.php?filename=01_05_1113042581371.gz)

---

### Post by ofnuts on 2011-08-12
> **ajits said:**
> where can I get more terminal command and it use?:D
[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

---

### Post by Drenriza on 2011-08-12
go to a terminal and type
```
apropos keyword
```
keyword is = a word you want to search for. Try wifi. Apropos will then show you commands that are available for wifi.

---

### Post by SidebySide on 2011-08-12
#Bash Reference Manual
[COLOR=RoyalBlue]wget[/COLOR] [http://www.gnu.org/software/bash/manual/bashref.pdf](http://www.gnu.org/software/bash/manual/bashref.pdf)
#[COLOR=Red](wget is a known command for terminal which it allows you to download a file via terminal, another one is axel, more powerful than wget.
[COLOR=Black]#[COLOR=Red]C[/COLOR][/COLOR]reate a script to download all these links in 1st try! to creat an script, copy & paste whole links, given here, to an text editor and save the file this form:[/COLOR] [COLOR=SeaGreen]NAME.sh[/COLOR]
#[COLOR=Red]Then go to terminal and use this command: [/COLOR][COLOR=SeaGreen]chmod +x NAME.sh[/COLOR] [COLOR=Red]that make saved file as an executable one
[COLOR=Black]#[/COLOR]Then type  [/COLOR][COLOR=SeaGreen]./NAME.sh [/COLOR][COLOR=Red]to start downloading[/COLOR][COLOR=SeaGreen][/COLOR][COLOR=Red])[/COLOR]
#
#
#Bash Guide for Beginners
wget [http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf](http://tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf)
#Advanced Bash-Scripting Guide
wget [http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
wget -cpk -nd [http://en.wikipedia.org/wiki/Comparison_of_command_shells](http://en.wikipedia.org/wiki/Comparison_of_command_shells)
#
#Cheat-sheets
wget [http://slash7.com/cheats/form_helpers.pdf](http://slash7.com/cheats/form_helpers.pdf)
wget [http://columbia.edu/~thl2102/linuxrefcard.pdf]("http://columbia.edu/%7Ethl2102/linuxrefcard.pdf")
wget [http://tangosoft.com/refcard/refcard-en-a4.pdf](http://tangosoft.com/refcard/refcard-en-a4.pdf)
wget [http://files.fosswire.com/2008/04/ubunturef.pdf](http://files.fosswire.com/2008/04/ubunturef.pdf)
wget [http://packetlife.net/media/library/12/tcpdump.pdf](http://packetlife.net/media/library/12/tcpdump.pdf)
wget [http://slash7.com/cheats/rails_files_cheatsheet.pdf](http://slash7.com/cheats/rails_files_cheatsheet.pdf)
wget [http://files.fosswire.com/wpu/2007/08/fwunixref.pdf](http://files.fosswire.com/wpu/2007/08/fwunixref.pdf)
wget [http://www.shell-tips.com/sheets/bash-help-sheet.pdf](http://www.shell-tips.com/sheets/bash-help-sheet.pdf)
wget [http://slash7.com/cheats/activerecord_cheatsheet.pdf](http://slash7.com/cheats/activerecord_cheatsheet.pdf)
wget [http://www.catonmat.net/download/awk.cheat.sheet.pdf](http://www.catonmat.net/download/awk.cheat.sheet.pdf)
wget [http://www.mikeoliveri.com/utils/shellcheatsheet.pdf](http://www.mikeoliveri.com/utils/shellcheatsheet.pdf)
wget [http://www.tablespace.net/quicksheet/aix-quicksheet.pdf](http://www.tablespace.net/quicksheet/aix-quicksheet.pdf)
wget [http://www.tablespace.net/quicksheet/apv-quicksheet.pdf](http://www.tablespace.net/quicksheet/apv-quicksheet.pdf)
wget [http://pragmaticstudio.com/rails/RailsTextMateCheats.pdf](http://pragmaticstudio.com/rails/RailsTextMateCheats.pdf)
wget [http://danleff.net/downloads/linux/linux_quick_ref_card.pdf](http://danleff.net/downloads/linux/linux_quick_ref_card.pdf)
wget [http://www.tablespace.net/quicksheet/solaris-quicksheet.pdf](http://www.tablespace.net/quicksheet/solaris-quicksheet.pdf)
wget [http://topfunky.com/clients/rails/ruby_and_rails_assertions.pdf](http://topfunky.com/clients/rails/ruby_and_rails_assertions.pdf)
wget [http://www.testingeducation.org/conference/wtst3_pettichord9.pdf](http://www.testingeducation.org/conference/wtst3_pettichord9.pdf)
wget [http://www.catonmat.net/download/sed.stream.editor.cheat.sheet.pdf](http://www.catonmat.net/download/sed.stream.editor.cheat.sheet.pdf)
wget [http://packetlife.net/media/library/13/Wireshark_Display_Filters.pdf](http://packetlife.net/media/library/13/Wireshark_Display_Filters.pdf)
wget [http://www.digilife.be/quickreferences/QRC/Vi%20Reference%20Card.pdf](http://www.digilife.be/quickreferences/QRC/Vi%20Reference%20Card.pdf)
wget [http://www.digilife.be/quickreferences/QRC/vi%20Quick%20Reference.pdf](http://www.digilife.be/quickreferences/QRC/vi%20Quick%20Reference.pdf)
wget [http://www.digilife.be/quickreferences/QRC/GDB%20Quick%20Reference.pdf](http://www.digilife.be/quickreferences/QRC/GDB%20Quick%20Reference.pdf)
wget [http://www.sans.org/security-resources/sec560/netcat_cheat_sheet_v1.pdf](http://www.sans.org/security-resources/sec560/netcat_cheat_sheet_v1.pdf)
wget [http://slash7.com/assets/2006/10/8/RJS-Demistified_Amy-Hoy-slash7_1.pdf](http://slash7.com/assets/2006/10/8/RJS-Demistified_Amy-Hoy-slash7_1.pdf)
wget [http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf](http://www.digilife.be/quickreferences/QRC/VIM%20Quick%20Reference%20Card.pdf)
wget [http://www.blainekendall.com/uploads/RubyOnRails-Cheatsheet-BlaineKendall.pdf](http://www.blainekendall.com/uploads/RubyOnRails-Cheatsheet-BlaineKendall.pdf)
wget [http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf](http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf)
wget [http://www.digilife.be/quickreferences/QRC/LINUX%20Admin%20Quick%20Reference.pdf](http://www.digilife.be/quickreferences/QRC/LINUX%20Admin%20Quick%20Reference.pdf)
wget [http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf](http://www.digilife.be/quickreferences/QRC/UNIX%20commands%20reference%20card.pdf)
wget [http://www.digilife.be/quickreferences/QRC/LINUX%20System%20Call%20Quick%20Reference.pdf](http://www.digilife.be/quickreferences/QRC/LINUX%20System%20Call%20Quick%20Reference.pdf)
wget [http://www.digilife.be/quickreferences/QRC/Linux%20Security%20Quick%20Reference%20Guide.pdf](http://www.digilife.be/quickreferences/QRC/Linux%20Security%20Quick%20Reference%20Guide.pdf)
wget [http://www.catonmat.net/blog/wp-content/plugins/wp-downloadMonitor/user_uploads/awk.cheat.sheet.pdf](http://www.catonmat.net/blog/wp-content/plugins/wp-downloadMonitor/user_uploads/awk.cheat.sheet.pdf)
wget [http://tangosoft.com/refcard/refcard-en-lt.pdf](http://tangosoft.com/refcard/refcard-en-lt.pdf)
wget [http://www.suso.com/infosheets/shell-commands20050327.png](http://www.suso.com/infosheets/shell-commands20050327.png)
wget [http://www.gnome-look.org/CONTENT/content-files/119833-cheat-cube-ub.svg.bz2](http://www.gnome-look.org/CONTENT/content-files/119833-cheat-cube-ub.svg.bz2)
wget [http://gnome-look.org/CONTENT/content-files/121377-cubo-trucos-ubuntu.pdf](http://gnome-look.org/CONTENT/content-files/121377-cubo-trucos-ubuntu.pdf)

---

### Post by debd on 2011-08-12
or you can use 
```
less /usr/bin
``` to know programs that are installed in your system..  I bet you'll find many new and amazing ones. Once you find a name interesting see its man page with ```
man <command>
``` ;)

---

### Post by SidebySide on 2011-08-26
[Linux Shell Scripting with Bash.pdf]("http://bib.tiera.ru/b/22893")  4.5 MB

[Linux Shell Scripting Tutorial.pdf]("http://bib.tiera.ru/b/9419")  0.2 MB

[Advanced Bash Scripting Guide, An in depth exploration of the gentle art of shell scripting.pdf]("http://bib.tiera.ru/b/30303")  0.9 MB

[Mastering UNIX Shell Scripting.pdf]("http://bib.tiera.ru/b/25826")  4.3 MB

[Wicked Cool Shell Scripts, 101 Scripts for Linux, Mac OS X, and Unix Systems.chm]("http://bib.tiera.ru/b/27544")  1.4 MB

[Shell Scripting Recipes, A Problem-Solution Approach.pdf]("http://bib.tiera.ru/b/24859")  2.4 MB

[Classic shell scripting.rar]("http://bib.tiera.ru/b/72546")  1.0 MB
[Classic Shell Scripting.chm]("http://bib.tiera.ru/b/18951")  1.0 MB

[Beginning Shell Scripting.pdf]("http://bib.tiera.ru/b/14961")  8.8 MB

++ I'm not responsible for their LICENSES. Check yourself.

---

