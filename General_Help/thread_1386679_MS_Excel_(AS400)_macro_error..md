---
title: "MS Excel (AS400) macro error."
date: 2010-01-21
forum: General Help
---

### Post by dilshannet on 2010-01-21
can anybody convert this macro to run on Linux with openoffice?

Rem Attribute VBA_ModuleType=VBAModule
Option VBASupport 1
Sub Macro1()
'
' Macro1 Macro
' Macro recorded 12/29/2006 by Your User Name
'

'
    With ActiveSheet.QueryTables.Add(Connection:=Array(Array( _
        "ODBC;DRIVER={Client Access ODBC Driver (32-bit)};PKG=QGPL/DEFAULT(IBM),2,0,1,0,512;LANGUAGEID=ENU;DFTPKGLIB=QGPL;DBQ=QGPL;SYSTEM=UAL" _
        ), Array("G;")), Destination:=Range("A2"))
        .CommandText = Array("SELECT * FROM ""QGPL"".""BC.CLMOT""")
        .Name = "AS400ODBC_4"
        .FieldNames = False
        .RowNumbers = False
        .FillAdjacentFormulas = False
        .PreserveFormatting = True
        .RefreshOnFileOpen = False
        .BackgroundQuery = True
        .RefreshStyle = xlInsertDeleteCells
        .SavePassword = False
        .SaveData = True
        .AdjustColumnWidth = False
        .RefreshPeriod = 0
        .PreserveColumnInfo = True
        .SourceConnectionFile = _
        "C:\Program Files\Common Files\ODBC\Data Sources\AS400ODBC.dsn"
        .Refresh BackgroundQuery:=False
    End With
End Sub

---

