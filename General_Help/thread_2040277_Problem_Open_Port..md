---
title: "Problem Open Port."
date: 2012-08-10
forum: General Help
---

### Post by mbm1234 on 2012-08-10
Hello, I don't know if this is the right place to ask this question, I have an issue when I try to connect to Firebird database in Linux Ubuntu version 12.04, here my source code:

procedure TFrmTest.DataBaseConnection;
begin
     with DataModuleTest.IBConnectionTest Do try
        {$IFDEF WIN32}
        DatabaseName:= StrDataBasePath + '\' + StrDataBaseName;
        {$ENDIF}
        {$IFDEF LINUX}
        DatabaseName:= StrDataBasePath + '/' + StrDataBaseName;
        {$ENDIF}
        Transaction := SQLTransactionTest;
        UserName:= StrUserName;
        Password:= StrPassword;
        HostName := '';
        Connected:= True;
        SQLQueryTest.DataBase := DataModuleTest.IBConnectionTest;
     except
          on ErrHandle: Exception Do
          begin
               ErrHandle.Create(ErrHandle.Message);
          end;
     end;
end;

Before I try to connect to Firebird database, my program read a XML file, this XML file has all data that Firebird database needs for connection.
And this is the message error:

Project Test raised exeption Class 'EIBDatabaseError' with message:
IBConnectionTest: DoInternalConnect:
-I/O error during "open" operation for file: "/admin/Documents/Test/TEST.GDB"
-Error while trying to open file.
-Permission denied

I execute in the Console this command:

chmod 766 admin
chmod 766 Documents
chmod 766 Test
chmod 766 TEST.GDB

but it's not working.
Also I execute command telnet 127.0.0.1 3050 and Firebird database is listening.

I compile this program in Linux Open Suse and Windows 7, the program works perfectly in Linux Open Suse and Windows 7.
Only on Linux Ubuntu has problem.

Please if somebody can help me, thanks in advance.

---

### Post by rukiaEnix on 2012-08-10
It's all about permissions.

What user is the owner of these files or directories?:

admin
Documents
Test
TEST.GDB

And what user is the owner of the script you are trying to run for the database connection?

---

### Post by mbm1234 on 2012-08-10
Hello rukiaEnix, thank you for reply, the owner of these folders and file is the user admin.

with the user admin I execute my program.

and now I did this:

chmod 777 admin
chmod 777 Documents
chmod 777 Test
chmod 777 TEST.GDB

I can connect to Firebird database, and my program works, but I think this setup is dangerous.

I do not want to give totally permission to my forlder and file, How can I fix this problem?.

---

### Post by mbm1234 on 2012-08-12
Hello, I did it!, I solve the problem, thank you.

---

### Post by rukiaEnix on 2012-08-13
If you can please post how you solved it and change the thread as solved!

Happy to hear it worked! :)

---

