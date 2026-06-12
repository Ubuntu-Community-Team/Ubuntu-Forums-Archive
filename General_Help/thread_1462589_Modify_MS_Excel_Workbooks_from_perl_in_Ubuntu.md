---
title: "Modify MS Excel Workbooks from perl in Ubuntu"
date: 2010-04-25
forum: General Help
---

### Post by luke_devon on 2010-04-25
Hi Friends
   
  After longs days and struggling on ubuntu to install some perl modules, I thought its better idea that if I could discuss with experts in ubuntu forum about my requirement. Actually I didn’t wanted to bother you guys by asking simple questions .but today I am failed and I need your help to proceed.
   
  I wanted to modify existing excel workbook by using Perl. Please find my requirement as it is basic in perl.
   
  1. Open existing Excel workbook in perl ( OS is ubuntu )
   
  2. Delete an unwanted excel sheet ( Eg: Sheet1 )
   
  3. Insert/copy some excel data into selected range of cells ( Eg: Suppose there is value, Ubuntu in CELL A1 . This value I wanted to copy until CELL A10. That’s meant value should be repeated until 10th Cell in A )
   
  4. Delete few selected rows.
   
  I googled to find out certain examples. But there is only few recognised perl modules exist in perl CPAN.
   
  Spreadsheet::WriteExcel,
  Spreadsheet::ParseExcel,   ..... As per my understanding these two are to create excel workbooks not to open an existing workbook.
   
  Win32::OLE .... On this perl module there are good tutorials but this is for MS Windows.
   
  Could you please help me to do this perl script in ubuntu ? after completion of the script i wanted to put this perl script live  in my production server ( RedHat Linux )



Thanks in Advance
Luke

---

### Post by blueridgedog on 2010-04-25
You are not likely to get that level of perl help on the Ubuntu form.  I have some suggestions:

1.  Write the author of the modules you will be using, he may have examples you can use:  [http://search.cpan.org/~szabgab/](http://search.cpan.org/~szabgab/)

2.  Look at the example on the IBM website: [http://www.ibm.com/developerworks/linux/library/l-pexcel/](http://www.ibm.com/developerworks/linux/library/l-pexcel/)

3.  Post in a perl forum ([http://cpanforum.com/](http://cpanforum.com/) and many others).

Good luck.

---

