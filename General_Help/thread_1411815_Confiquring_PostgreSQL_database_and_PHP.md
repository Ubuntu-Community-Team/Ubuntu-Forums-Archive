---
title: "Confiquring PostgreSQL database and PHP"
date: 2010-02-20
forum: General Help
---

### Post by undrakh_orgil on 2010-02-20
tables and entry
***************************** 


CREATE TABLE DOCTOR(DOC_NO INTEGER PRIMARY KEY, DOC_NAME TEXT, ADDRESS TEXT, CITYNAME TEXT,AREA TEXT);

CREATE TABLE HOSPITAL(HOSP_NO INTEGER PRIMARY KEY, HOSP_NAME TEXT,HOSP_CITY TEXT);

CREATE TABLE DH(DOC_NO INTEGER,FOREIGN KEY(DOC_NO) REFERENCES DOCTOR(DOC_NO), HOSP_NO INTEGER,FOREIGN KEY(HOSP_NO) REFERENCES HOSPITAL(HOSP_NO));

INSERT INTO DOCTOR VALUES(1,'AJIT','NIGDI','PUNE','A');
INSERT INTO DOCTOR VALUES(2,'ANIL','PIMPRI','PUNE','B');
INSERT INTO DOCTOR VALUES(3,'AMIT','CHINCHWAD','MUMBAI','C');
INSERT INTO DOCTOR VALUES(4,'JAY','PRADHIKARAN','PUNE','D');
INSERT INTO DOCTOR VALUES(5,'RAM','KALEWADI','PUNE','E');
INSERT INTO DOCTOR VALUES(6,'SHAM','KHADKI','PUNE','F');
INSERT INTO DOCTOR VALUES(7,'NARESH','DAPODI','MUMBAI','A');
INSERT INTO DOCTOR VALUES(8,'PRIYA','BHOPODI','MUMBAI','D');

INSERT INTO HOSPITAL VALUES(1,'JIJAMATA','PUNE');
INSERT INTO HOSPITAL VALUES(2,'RUBI','PUNE');
INSERT INTO HOSPITAL VALUES(3,'K.E.M','MUMBAI');
INSERT INTO HOSPITAL VALUES(4,'YCM','PUNE');

INSERT INTO DH VALUES(1,2);
INSERT INTO DH VALUES(2,1);
INSERT INTO DH VALUES(3,3);
INSERT INTO DH VALUES(4,4);
INSERT INTO DH VALUES(5,2);
INSERT INTO DH VALUES(6,3);
INSERT INTO DH VALUES(7,1);
INSERT INTO DH VALUES(2,2);
INSERT INTO DH VALUES(2,3);
INSERT INTO DH VALUES(5,3);
INSERT INTO DH VALUES(4,4);
INSERT INTO DH VALUES(5,1);
INSERT INTO DH VALUES(6,2);
INSERT INTO DH VALUES(1,1);

***************************** 

HTML code

***************************** 

<form method='POST' action='hosp_doc_db.php'> 
<pre>ENTER THE HOSPITAL NAME:-<input type =text name='hosp'></pre> 
<input type ='SUBMIT'> 
<input type ='RESET'> 
</FORM> 
 


***************************** 

PHP code

***************************** 

<?      include_once('DB.php');
         $db = db::connect("pgsql://root:postgres@localhost/orgio");
        if(DB::isError($db))
        {
                echo"db not connect";
                die($db->getMessage());
        }
        $hn=$_POST['hosp'];
        $sql="select doctor.doc_no,doc_name,address,cityname,area
                from doctor,hospital,dh
                where doctor.doc_no=dh.doc_no
                 and  hospital.hosp_no=dh.hosp_no
                 and hosp_name='$hn'";
        $q=$db->query($sql);
        if(DB::isError($q))
        {
                die($db->getMessage());
        }
        $head=array('Doc No','Doc Name','Address','city','Area');
 echo'<table border=1>';
        echo'<tr>';
        foreach($head as $val)
          echo"<th>$val</th>";
          echo'<tr>';
          while($row=$q->fetchrow())
          {
           echo'<tr>';
           foreach($row as $val)
           {
            echo"<td>$val</td>";
           }
          }
             $q->free();
         $db->disconnect();
?>


***************************** 
WHEN I EXECUTE IT I M GETTING

db not connectDB Error: connect failed

I know that some configuration must be done. But i don't know that settings in UBUNTU pls help me.

---

