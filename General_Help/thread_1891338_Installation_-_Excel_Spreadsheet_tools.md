---
title: "Installation - Excel Spreadsheet tools"
date: 2011-12-05
forum: General Help
---

### Post by OldManRiver on 2011-12-05
All,

Installing the Excel Spreadsheet tool from Zend HOWTO at:

> [http://devzone.zend.com/27/reading-and-writing-spreadsheets-with-php/](http://devzone.zend.com/27/reading-and-writing-spreadsheets-with-php/)

on the company Ubuntu Intranet server.

Keep getting the errors:

> Fatal error: Cannot redeclare class Spreadsheet_Excel_Writer in /usr/share/php/Spreadsheet/Excel/Writer.php on line 103

Not sure what is causing this error and think I have a conflict between the two programs listed in the HOWTO.

Did not find any help forums for the 2 tools in the HOWTO, but will be checking the #pear channel on IRC to see what other help is available, but needed to document this so can direct any possible gurus to this write-up.

All help appreciated.

Thanks!

OMR

---

### Post by OldManRiver on 2011-12-06
All,

Found a new and better tool @:

[http://phpexcel.codeplex.com](http://phpexcel.codeplex.com)

But after installing it, found the "Autoloader.php" is not working right so getting this error:

> Found==> PHPExcel_Autoloader
11:01:50 Create new PHPExcel object
Fatal error: Class 'PHPExcel_Worksheet' not found in /usr/share/php/PHPExcel/PHPExcel.php on line 109
I put the echo statement in the Autoloader producing the first line and am calling with code:```
<?php
// file test01.php

/** Error reporting */
error_reporting(E_ALL);

/** Include path **/
$n_path = ':/usr/share/php/PHPExcel/:/usr/share/php/Spreadsheet/Excel;../Classes/';
//$n_path = ':/usr/share/php/PHPExcel/;../Classes/';
ini_set('include_path', ini_get('include_path').$n_path);

/** PHPExcel */
include 'PHPExcel.php';

/** PHPExcel_Writer_Excel2007 */
include 'PHPExcel/Writer/Excel2007.php';

// Create new PHPExcel object
echo date('H:i:s') . " Create new PHPExcel object\n";
$objPHPExcel = new PHPExcel();

// Set properties
echo date('H:i:s') . " Set properties\n";
$objPHPExcel->getProperties()->setCreator("Maarten Balliauw");
$objPHPExcel->getProperties()->setLastModifiedBy("Maarten Balliauw");
$objPHPExcel->getProperties()->setTitle("Office 2007 XLSX Test Document");
$objPHPExcel->getProperties()->setSubject("Office 2007 XLSX Test Document");
$objPHPExcel->getProperties()->setDescription("Test document for Office 2007 XLSX, generated using PHP classes.");


// Add some data
echo date('H:i:s') . " Add some data\n";
$objPHPExcel->setActiveSheetIndex(0);
$objPHPExcel->getActiveSheet()->SetCellValue('A1', 'Hello');
$objPHPExcel->getActiveSheet()->SetCellValue('B2', 'world!');
$objPHPExcel->getActiveSheet()->SetCellValue('C1', 'Hello');
$objPHPExcel->getActiveSheet()->SetCellValue('D2', 'world!');

// Rename sheet
echo date('H:i:s') . " Rename sheet\n";
$objPHPExcel->getActiveSheet()->setTitle('Simple');


// Save Excel 2007 file
echo date('H:i:s') . " Write to Excel2007 format\n";
$objWriter = new PHPExcel_Writer_Excel2007($objPHPExcel);
$objWriter->save(str_replace('.php', '.xlsx', __FILE__));

// Echo done
echo date('H:i:s') . " Done writing file.\r\n";
```
I had to create the var $n_path and add the additional values of:> :/usr/share/php/PHPExcel/:/usr/share/php/Spreadsheet/Excel
compared with the old commented out value of ";../Classes/" from the example on the HOWTO page.

I have been able to get around some of the problem with manual loads in the test01.php file of:```
include 'PHPExcel.php';
include 'PHPExcel/IComparable.php';
include 'PHPExcel/Worksheet.php';

```

Sorry but I've not been able to debug the autoloader process and need some help with it.

Thanks!

OMR

---

### Post by OldManRiver on 2011-12-07
All,

Can I get some help here?

Thanks!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #19 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by dino99 on 2012-06-08
simply check the "thread tools" on top right of each thread

---

