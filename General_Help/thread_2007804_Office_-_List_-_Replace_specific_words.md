---
title: "Office - List - Replace specific words"
date: 2012-06-21
forum: General Help
---

### Post by Hitlist on 2012-06-21
Hello,   

following situation:  

   I have one large Spreadsheetfile with a few columns of Information and I need to replace some entries with updated Information from a second file.  The problem is that there is no type of order.   

 It`s a Databasetype File like:  

  File 1 (example): 

 Song        |     Year | Size    | Filename     |  
Remember    |  1993    |  3,8mb  |  RandomX12   |     
Remember    |  1993    |  3,8mb  |  RandomX53   |   
Remember    |  1993    |  3,8mb  |  Randomf1d   |     
Remember    |  1993    |  3,8mb  |  Randomhdb   |   
Remember    |  1993    |  3,8mb  |  RandomM62   |     
Remember    |  1993    |  3,8mb  |  Random043   |   
Remember    |  1993    |  3,8mb  |  RandomP1N   |     
Remember    |  1993    |  3,8mb  |  RandomG5k   |     



 File2 (example): 

 RandomX12:addedInfo(edf) 
RandomX53:addedInfo(hdjh) 
Randomf1d:addedInfo(efrv) 
Randomhdb:addedInfo(vroi) 
RandomM62:addedInfo(krjwvch) 
Random043:addedInfo(rand12c)


  I need to replace some of the names with the full line of the matching second file.  

  This: 
Remember    |  1993    |  3,8mb  |  RandomX12   |   

  Must become this: 
Remember    |  1993    |  3,8mb  |  RandomX12:addedInfo(edf)   |      


Now lets say there are like 100k entries from witch 70k must be replaced. Doing it by hand isn`t an option.  I need a tool that searches all names for matches in file 2 and replace the old entry with the full line with the matching string.    

Did someone know how to do this?    

thanks

---

### Post by Hitlist on 2012-06-21
Maybe there is a way doing it with the terminal?

 I could open the second file and replace the : with some statements and add some command at the beginning and/or ending of each line.

 RandomX12:addedInfo 
Randomr52:addedInfo 
RandomH3a:addedInfo 

 Could easily become this:

 &quot;open file1 && search for RandomX12 && replace it with addedInfo&quot; 
&quot;open file1 && search for Randomr52 && replace it with addedInfo&quot; 
&quot;open file1 && search for RandomH3a && replace it with addedInfo&quot;

 How to do it?

---

### Post by drmrgd on 2012-06-21
I'm not sure how comfortable in Excel (or Libre Office's version).  If you prefer to stick with the spreadsheet, I think the easiest way to do it is by splitting apart the File 2 example, and then using the information for a vlookup.  I'm going to assume that when you typed the '|' character, you were indicating individual columns and that the data in File 1 is in 4 columns.  

So, in your example.

1. Copy File 2 to a new tab within File 1 (I'm going to assume that all of the data starts in A1 and is in 1 column).

2. Add 1 empty column in A so that the data moves to column B.

2. Split apart the string by entering (in A1) '=LEFT(B1,FIND(":", B1, 1)-1)'.  This should output RandomX12.  In C1 enter '=RIGHT(B1,LEN(B1)-FIND(":", B1, 1))'.  This should output addedInfo(edf).

3.  Now you should have 3 columns of data, and we'll use this to attach the string you want to the File 1 dataset.  Go back to the first tab with that data, and in the first cell of last column, enter =VLOOKUP(D1,<highlight the whole table with your data you made above,3,0).  That should output the data we just split out in column 3 based on the data in the 4 column.  So, you should get 'addedInfo(edf)' in the very next cell to RandomX12.


It's a lot of steps, and it might be a little easier with awk or sed in the terminal, but this is how to do it in Excel.

---

### Post by Hitlist on 2012-06-21
Hello,

 thanks. 

 How to do that with with more than 1 row?  

 The file with the 4 columns is about 100k rows. The file with the updated Info is about 70k rows.

 It does not need to be an office way. A way to do this with the terminal is fine too.

 I`m not very deep into Office.

---

### Post by drmrgd on 2012-06-21
> **Hitlist said:**
> Hello,

 thanks. 

 How to do that with with more than 1 row?  

 The file with the 4 columns is about 100k rows. The file with the updated Info is about 70k rows.

 It does not need to be an office way. A way to do this with the terminal is fine too.

 I`m not very deep into Office.

Sorry, I forgot to address that.  Once you have the formula working as you want it, you just have to copy it into all of the cells in the column for each row that you need.  The one catch to look out for is to make sure that when you copy the final vlookup formula, that the reference to the table in the second tab is static and not dynamic.  In other words, the cell reference should look like $A$1:$C$70000 (or whatever the range is), and not A1:C70000.  If you leave it as dymanic, you'll see that the table reference will keep sequentially changing as you move down the column, which means you'll end up referencing the wrong cells.  

Something like this is definitely doable with something like sed or awk in the terminal.  However, my awk skills are not quite sharp enough to give the best way to do it.  A more skilled BASH expert may chime in with a more simple way to do it, although for me (and since your data is already in a spreadsheet), this is something that can be done in just a minute knowing some simple Excel formulas.

---

### Post by Hitlist on 2012-06-21
The problem is that I need to do the left and right split for every row/cell. The example shows how to do it with the first row/cell?

 Another problem is that I have to add the cellname to the Vlookup like:

 =VLOOKUP(H2029,A1:C70000,3,0)

=VLOOKUP(H2030,A1:C70000,3,0)

 Is there an option with autoincremetion?

 Like selecting the whole column an insert the command just one time and with every row it gets auto +1 in the needed parts?

 Sorry if I`m just misunderstanding.

---

### Post by Hitlist on 2012-06-21
Hello,  written it in C. There are 3 Output files which numerates all needed parts from 0 to 100k. 

 :)  ```
/* 
=LEFT(B1,FIND(&quot;:&quot;, B1, 1)-1)
=RIGHT(B1,LEN(B1)-FIND(&quot;:&quot;, B1, 1)) 
=VLOOKUP(D1,$A$1:$C$70000,3,0)

 compile it with:

gcc -c '/path/to/folder/counter.c'
gcc -o numerator '/path/to/folder/counter.o'
*/

#include stdio.h> 
#include fcntl.h> 
#include unistd.h> 

 int main()

       {
    int a;
    FILE *fp,*fd,*fe;
    fp=fopen(&quot;/path/to/folder/output.txt&quot;, &quot;w&quot;);
    fd=fopen(&quot;/path/to/folder/output2.txt&quot;, &quot;w&quot;);
    fe=fopen(&quot;/path/to/folder/output3.txt&quot;, &quot;w&quot;);

     for( a = 0; a < 100000; a++ )
        {
        printf( &quot;%d\n&quot;,a);
        sleep(0);
        fprintf(fp, &quot;=LEFT(B%d,FIND(\&quot;:\&quot;, B%d, 1)-1)\n&quot;,a,a);
        fprintf(fd, &quot;=RIGHT(B%d,LEN(B%d)-FIND(\&quot;:\&quot;, B%d, 1)) \n&quot;,a,a,a);
        fprintf(fe, &quot;=VLOOKUP(D%d,CD70000,3,0)\n&quot;,a);
        }
        fclose(fp);
        fclose(fd);
        fclose(fe);

      }

```Something goes wrong here.   

```
Remove all &quot;  

and put a < in front of stdio.h>,fcntl.h>,unistd.h> 
``` Replace CD70000 with the values you want.  Who is that guy posting above me?

---

### Post by erind on 2012-06-21
> **Hitlist said:**
> Hello,   

following situation:  

   I have one large Spreadsheetfile with a few columns of Information and I need to replace some entries with updated Information from a second file.  The problem is that there is no type of order.   

 It`s a Databasetype File like:  

  File 1 (example): 

 Song        |     Year | Size    | Filename     |  
Remember    |  1993    |  3,8mb  |  RandomX12   |     
Remember    |  1993    |  3,8mb  |  RandomX53   |   
Remember    |  1993    |  3,8mb  |  Randomf1d   |     
Remember    |  1993    |  3,8mb  |  Randomhdb   |   
Remember    |  1993    |  3,8mb  |  RandomM62   |     
Remember    |  1993    |  3,8mb  |  Random043   |   
Remember    |  1993    |  3,8mb  |  RandomP1N   |     
Remember    |  1993    |  3,8mb  |  RandomG5k   |     



 File2 (example): 

 RandomX12:addedInfo(edf) 
RandomX53:addedInfo(hdjh) 
Randomf1d:addedInfo(efrv) 
Randomhdb:addedInfo(vroi) 
RandomM62:addedInfo(krjwvch) 
Random043:addedInfo(rand12c)


  I need to replace some of the names with the full line of the matching second file.  

  This: 
Remember    |  1993    |  3,8mb  |  RandomX12   |   

  Must become this: 
Remember    |  1993    |  3,8mb  |  RandomX12:addedInfo(edf)   |      


Now lets say there are like 100k entries from witch 70k must be replaced. Doing it by hand isn`t an option.  I need a tool that searches all names for matches in file 2 and replace the old entry with the full line with the matching string.    

Did someone know how to do this?    

thanks

One way with awk,

```
awk 'NR==FNR{ a[$1]=$0; next }
     { gsub(/^[ \t]+|[ \t]+$/,"",$4);
       if($4 in a) { $4=a[$4]; print $0 }
       else print $0 
     }
    ' FS=':' **[COLOR=Blue]File_2[/COLOR]** OFS='|' FS='|' **File_1**

```Which based on your sample files, yields:

```
Song | Year | Size |Filename|
Remember | 1993 | 3,8mb |RandomX12:addedInfo(edf)|
Remember | 1993 | 3,8mb |RandomX53:addedInfo(hdjh)|
Remember | 1993 | 3,8mb |Randomf1d:addedInfo(efrv)|
Remember | 1993 | 3,8mb |Randomhdb:addedInfo(vroi)|
Remember | 1993 | 3,8mb |RandomM62:addedInfo(krjwvch)|
Remember | 1993 | 3,8mb |Random043:addedInfo(rand12c)|
Remember | 1993 | 3,8mb |RandomP1N|
Remember | 1993 | 3,8mb |RandomG5k|

```

---

### Post by Hitlist on 2012-06-24
Hello,

I can`t get the awk way to work. The file is to big to use vlookup, so I have to use awk.

This is how the file which needs to get updated looks like. Just one line as example:
file1:

rocklandradio,sessionBCEold

and this is what the other file looks like (just one line):
file2:

sessionBCEold:sessionBCEnew



But as said. There are many lines with different content.





Maybe you can work that out for me?:)

---

### Post by col48 on 2012-06-24
A Spreadsheet method - probably the way I'd do it!

1. In fresh column in file 1 (say column H)
insert row numbers (so that the order of rows can be restored later, in step 6)
Do so in this way: in cell H1 insert 1
in cell H2 insert the formula =H1+1
copy cell H2 to cells H3 to Hxx where xx is the last row of data.
Now copy all the cells H1 to Hxx to the clipboard and do a Paste Special into the same place, pasting Numbers only

So in cols A-D you have your original data and in col H the row numbers, no longer as formulae.

2. In column D in file 2 (same column as data-to-be-replaced in file 1) 
in cell D1 insert the formula =LEFT(A1,FIND(":", A1)-1)
copy cell D1 to cells D2 to Dyy where yy is the last row of data.

3. Copy file 2's cells A1 to Dyy into columns A to D of file 1 below the data which is already there.

4. Now sort all the data in file 1 on columns D (main sort) and H (secondary sort).
This should bring all the entries from file 2 to immediately after the corresponding entries in file 1.

5.Now in cell E1 insert the formula =IF(D1=D2,A2,D1)
Copy cell E1 to cells E2 to Ezz where zz is the last row with any data in it.
You should now find that column E contains what you want wherever there is a row which came from file 1.
Fix the values by copying cells E1 to Ezz to the clipboard and doing a Paste Special into the same place, pasting Text only.

6. Sort all the data on column H
7. Delete all rows below row xx (which should be the one with the last row number entry in column H)
8. Delete columns H and D

Bingo!  Assuming anything in file 2 which does not have a corresponding file 1 row is to be discarded.

Complex but it is possible to correct any problems as you go along.

---

