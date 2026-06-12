---
title: "bash: line 60: fg: no job control"
date: 2012-01-24
forum: General Help
---

### Post by cedardoc on 2012-01-24
I have no formal programming training but have been cutting and pasting scripts together for a year or so and have never come up with this error.  Its in a function that I pasted in and modified from another script that still works well.  When I commend out lines, I've noticed it only comes up on or just before lines that have multiple commands on it.

here's the function (yad is a bash gui thing, like zenity but better):
```

#-----------------------------------------function: <add todo>
function addTodo () {
theTask=" $1"
theTask=`echo $theTask | awk '{gsub(/\(/,"[");print}'`
theTask=`echo $theTask | awk '{gsub(/\)/,"]");print}'`; echo the Task is $theTask $cr
theNotes="$2"
theNotes=`echo $theNotes | awk '{gsub(/\(/,"[");print}'`
theNotes=`echo $theNotes | awk '{gsub(/\)/,"]");print}'`; echo the annotation is $theNotes
theProject="$3";[[ $theProject == *none* ]] && theProject="" || theProject=" +$theProject";[[ $theProject="+(null)" && theProject="" ]]; echo the Project is $theProject $cr;
theDate="$4"; 
useDate="$5"; 
echo ----
[[ "$todaysDate" = "$theDate" ]] && echo "they're not the same" && useDate="TRUE";
(line 60)theDate=" due:$theDate";
[[ $useDate = "FALSE" ]] && theDate="" && echo the date is false false false
echo the Date is $theDate $cr;
echo ----
echo  usedate is $useDate
thePriority="$6";[[ $thePriority = "." ]] && thePriority="";[[ $thePriority != "" ]] && thePriority="$thePriority";echo the Priority is $thePriority $cr
randomContext="$7"
tHome="$8";[[ $tHome = "FALSE" ]] && tHome="" || tHome=" @home";echo the tHome is $tHome $cr
tWork="$9";[[ $tWork = "FALSE" ]] && tWork="" || tWork=" @work";echo the tWork is $tWork $cr
shift ;tPts="$9";[[ $tPts = "FALSE" ]] && tPts="" || tPts=" @pts";echo the tPts is $tPts $cr
shift ;tErrands="$9";[[ $tErrands = "FALSE" ]] && tErrands="" || tErrands=" @errands";echo the tErrands is $tErrands $cr
shift ;tFreetime="$9";[[ $tFreetime = "FALSE" ]] && tFreetime="" || tFreetime=" @freetime";echo the tFreetime is $tFreetime $cr
shift ;tYard="$9";[[ $tYard = "FALSE" ]] && tYard="" || tYard=" @yard";echo the tYard is $tYard $cr
shift ;tCity="$9";[[ $tCity = "FALSE" ]] && tCity="" || tCity=" @city";echo the tCity is $tCity $cr
shift ;tLinks="$9";[[ $tLinks = "FALSE" ]] && tLinks="" || tLinks=" @links";echo the tLinks is $tLinks $cr
shift ;tReport="$9";echo the report format is $tReport $cr

# for "add to this list" button in next script:
echo $theProject$theDate$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks > /home/david/Dropbox/todoTxt/.add2ThisList.txt
newTask="bash todo.sh -d /home/david/Dropbox/todoTxt/todo.cfg add $theTask$theProject$theDate$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks" %15
echo the new task is: $newTask$cr-----------------$cr
#-- for annotations
taskResponse=`eval $newTask`
echo the response is $taskResponse
pkill yad
}
export -f addTodo

```
any suggestions?

---

### Post by drmrgd on 2012-01-24
Would you mind reposting this code using the code tags?  It's brutal trying to read non-formatted code like this, and will make the job of finding the problem a lot easier.

---

### Post by cedardoc on 2012-01-24
> **drmrgd said:**
> Would you mind reposting this code using the code tags?  It's brutal trying to read non-formatted code like this, and will make the job of finding the problem a lot easier.

(this is now solved - see note at end)

woops sorry.  I may as well put the entire thing in:

```

#!/bin/bash
#addTodo.sh
#gui that adds tasks to todo.txt (the Gina Tripani todo.txt script thing)
#

cr="
"
fromAScript=$1
theText="task text"
echo the string from another script is:$fromAScript
[[ $fromAScript != "" ]] && theText=$fromAScript
#
# ----------------------------   get project list (works)
#

echo "none" > /home/david/Dropbox/todoTxt/.projects3.txt
bash todo.sh -d /home/david/Dropbox/todoTxt/todo.cfg listproj > /home/david/Dropbox/todoTxt/.projects1.txt
n=`cat /home/david/Dropbox/todoTxt/.projects1.txt | wc -l`; # how many lines are there?
sed 's/+//g' /home/david/Dropbox/todoTxt/.projects1.txt > /home/david/Dropbox/todoTxt/.projects2.txt

cat /home/david/Dropbox/todoTxt/.projects2.txt >> /home/david/Dropbox/todoTxt/.projects3.txt

echo `tr '\n' '!' < /home/david/Dropbox/todoTxt/.projects3.txt` > /home/david/Dropbox/todoTxt/.projects3.txt
projects=`cat /home/david/Dropbox/todoTxt/.projects3.txt`
# ------------------------------------------------</projects>
#

# -------------- get list of current contexts into $con (works)
#
echo "none" > /home/david/Dropbox/todoTxt/.con3.txt
bash todo.sh -d /home/david/Dropbox/todoTxt/todo.cfg listcon > .con1.txt
nl=`cat .con1.txt | wc -l`; # how many lines are there?
sed 's/@//g' /home/david/Dropbox/todoTxt/.con1.txt > /home/david/Dropbox/todoTxt/.con2.txt
cat /home/david/Dropbox/todoTxt/.con2.txt >> /home/david/Dropbox/todoTxt/.con3.txt
echo `tr '\n' '!' < /home/david/Dropbox/todoTxt/.con3.txt` > /home/david/Dropbox/todoTxt/.con3.txt
contexts=`cat /home/david/Dropbox/todoTxt/.con3.txt`

echo context list is: $contexts
#-----------------------------------------------------</contexts>

theDate=`date "+%Y-%0m-%0d"`
todaysDate=$theDate
echo todays date is $todaysDate


#-----------------------------------------function: <add todo>
function addTodo () {

theTask=" $1"
theTask=`echo $theTask | awk '{gsub(/\(/,"[");print}'`
theTask=`echo $theTask | awk '{gsub(/\)/,"]");print}'`; echo the Task is $theTask $cr
theNotes="$2"
theNotes=`echo $theNotes | awk '{gsub(/\(/,"[");print}'`
theNotes=`echo $theNotes | awk '{gsub(/\)/,"]");print}'`; echo the annotation is $theNotes
theProject="$3";[[ $theProject == *none* ]] && theProject="" || theProject=" +$theProject";[[ $theProject="+(null)" && theProject="" ]]; echo the Project is $theProject $cr;
theDate="$4"; 
useDate="$5"; 
echo ----
[[ "$todaysDate" = "$theDate" ]] && echo "they're not the same" && useDate="TRUE";
theDate=" due:$theDate";
[[ $useDate = "FALSE" ]] && theDate="" && echo the date is false
echo the Date is $theDate $cr;
echo ----
echo  usedate is $useDate
thePriority="$6";[[ $thePriority = "." ]] && thePriority="";[[ $thePriority != "" ]] && thePriority="$thePriority";echo the Priority is $thePriority $cr
randomContext="$7"
tHome="$8";[[ $tHome = "FALSE" ]] && tHome="" || tHome=" @home";echo the tHome is $tHome $cr
tWork="$9";[[ $tWork = "FALSE" ]] && tWork="" || tWork=" @work";echo the tWork is $tWork $cr
shift ;tPts="$9";[[ $tPts = "FALSE" ]] && tPts="" || tPts=" @pts";echo the tPts is $tPts $cr
shift ;tErrands="$9";[[ $tErrands = "FALSE" ]] && tErrands="" || tErrands=" @errands";echo the tErrands is $tErrands $cr
shift ;tFreetime="$9";[[ $tFreetime = "FALSE" ]] && tFreetime="" || tFreetime=" @freetime";echo the tFreetime is $tFreetime $cr
shift ;tYard="$9";[[ $tYard = "FALSE" ]] && tYard="" || tYard=" @yard";echo the tYard is $tYard $cr
shift ;tCity="$9";[[ $tCity = "FALSE" ]] && tCity="" || tCity=" @city";echo the tCity is $tCity $cr
shift ;tLinks="$9";[[ $tLinks = "FALSE" ]] && tLinks="" || tLinks=" @links";echo the tLinks is $tLinks $cr
shift ;tReport="$9";echo the report format is $tReport $cr

# for "add to this list" button in next script:
echo $theProject$theDate$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks > /home/david/Dropbox/todoTxt/.add2ThisList.txt
newTask="bash todo.sh -d /home/david/Dropbox/todoTxt/todo.cfg add $theTask$theProject$theDate$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks" %15
echo the new task is: $newTask$cr-----------------$cr

pkill yad
}
export -f addTodo

#-----------------------------------------</addTodo>

#---------------------------------------------------<cliEntry>
function cliEntry () {
theTask="task $1"; echo the Task is $theTask $cr
eval $theTask | yad --title "$cmd" --text-info --width 530 --height 400  --timeout 60 --show-uri &
}
export -f cliEntry

#----------------------------------------</cliEntry>

#-----------------------------------------------------<checklist>
function checklist () {
# assign the variables
theTask=" $1"; echo the Task is $theTask $cr
theNotes="$2"; echo the annotation is $theNotes
theProject="$3";[[ $theProject == *none* ]] && theProject="" || theProject=" pro:$theProject";[[ $theProject="pro:(null)" && theProject="" ]]; echo the Project is $theProject $cr
theDate="$4";[[ $todaysDate = $theDate ]] && theDate="" || theDate=" [$theDate]";echo the Date is $theDate $cr
useDate="$5"; [[ $useDate = "FALSE" ]] && theDate=""; echo the use date option is: $useDate
thePriority="$6";[[ $thePriority = "." ]] && thePriority="";[[ $thePriority != "" ]] && thePriority=" pri:$thePriority";echo the Priority is $thePriority $cr
tHome="$7";[[ $tHome = "FALSE" ]] && tHome="" || tHome=" +home";echo the tHome is $tHome $cr
tWork="$8";[[ $tWork = "FALSE" ]] && tWork="" || tWork=" +work";echo the tWork is $tWork $cr
tPts="$9";[[ $tPts = "FALSE" ]] && tPts="" || tPts=" +pts";echo the tPts is $tPts $cr
shift ;tErrands="$9";[[ $tErrands = "FALSE" ]] && tErrands="" || tErrands=" +errands";echo the tErrands is $tErrands $cr
shift ;tFreetime="$9";[[ $tFreetime = "FALSE" ]] && tFreetime="" || tFreetime=" +freetime";echo the tFreetime is $tFreetime $cr
shift ;tYard="$9";[[ $tYard = "FALSE" ]] && tYard="" || tYard=" +yard";echo the tYard is $tYard $cr
shift ;tCity="$9";[[ $tCity = "FALSE" ]] && tCity="" || tCity=" +city";echo the tCity is $tCity $cr
shift ;tLinks="$9";[[ $tLinks = "FALSE" ]] && tLinks="" || tLinks=" +links";echo the tLinks is $tLinks $cr
#DoneDel="${words[11]}";echo the message is $DoneDel
shift ;tReport="$9";echo the report format is $tReport $cr
# for "add to this list" button in next script:
echo $theProject$theDate$thePriority$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks > /home/david/Dropbox/todoTxt/.add2ThisList.txt
# prepare the checklist
cmd=$tReport$theProject$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks
[[ $tReport = "list" ]] && cmd="list $theTask$theProject$theDate$thePriority$tHome$tWork$tPts$tErrands$tFreetime$tYard$tCity$tLinks"
echo $cmd > /home/david/Dropbox/todoTxt/.reportTitle.txt
echo $cmd > /home/david/Dropbox/todoTxt/.reportTitle2.txt; # for "add to this list" in next script
echo ----------------!!!!!!!!!!!!!---------------
cat /home/david/Dropbox/todoTxt/.reportTitle.txt
cat /home/david/Dropbox/todoTxt/.reportTitle2.txt
#task command is ready to go to the script that processes the output
#but first, get the first line for columns:
eval task $cmd > /home/david/Dropbox/todoTxt/taskCols.txt 
#above is for the next script to deal with:
/home/david/Dropbox/todoTxt/task2YadListb.sh $cmd &
#pkill yad
}
export -f checklist
#------------------------------------------</checklist>

yad --title="New Task" --geometry=+500+50\
 --text="fill in the details for your new task" --always-print-result \
 --date-format="%Y-%0m-%0d" \
 --form --columns=3 --field="task text" \
 --field="notes" \
 --field="project:CB" \
 --field "date:dt" \
 --field "useDate:CHK" \
 --field="priority:CB" \
 --field="context:CB" \
 --field="home:CHK" \
 --field="work:CHK" \
 --field="pts:CHK" \
 --field="errands:CHK" \
 --field="freetime:CHK" \
 --field="yard:CHK" \
 --field="citytrip:CHK" \
 --field="links:CHK" \
 --field="report type:CB" \
 --field "addTask:BTN"  \
 --field "cliEntry:BTN"  \
 --field "checklist:BTN"  \
"$theText" "." "$projects" "$theDate" FALSE ".!A!B!C" "$contexts" FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE "newest!next!projects!tags!summary!list!" \
"bash -c 'addTodo \"%1\" \"%2\" %3 %4 %5 \"%6\" %7 %8 %9 %10 %11 %12 %13 %14 %15 %16'" \
"bash -c 'cliEntry \"%1\"'" \
"bash -c 'checklist \"%1\" \"%2\" %3 %4 %5 \"%6\" %7 %8 %9 %10 %11 %12 %13 %14 %15 %16'" \

output=`echo $?`
echo output is: $output

```

Like I mentioned, this is a bash gui with multiple buttons that run the various functions depending on which button is pressed, and while I haven't completed the other functions, the one with my job control error is the "addTodo" function.

I appreciate any help, and please excuse the mess - I'd imagine I'm ignoring all sorts of programming conventions (like all caps for variables - I'm sure there's more bad programming style in there than that)

Thanks, 
Dave

PS - I was just checking over things before I posted this and somehow a "%15" got thrown in to the end of one line, and that seemed to be the cause of it.

I'll leave this in case some other amateur does the same thing wrong as me :-)
now I just have to figure out how to mark this as SOLVED...

---

