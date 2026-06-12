---
title: "LibreOffice Should have a Number to English Words Function"
date: 2012-03-14
forum: General Help
---

### Post by Joliea on 2012-03-14
I do a lot of documents requiring me to write some figures in words and in numbers. I wish I would have a function in LibreOffice that would convert numbers to english words function. For example, convert the number 587 to "Five Hundred and Eighty Seven".

I know Microsoft Excel has this function somewhere, (see [http://support.microsoft.com/kb/213360](http://support.microsoft.com/kb/213360)) but I tried copying that code to LibreOffice and it didn't work. Since I know absolutely nothing about code... I can't do anything!

Help?!?


):P

---

### Post by PaulW2U on 2012-03-14
You could ask over at [http://user.services.openoffice.org/en/forum/](http://user.services.openoffice.org/en/forum/). 

LibreOffice is also supported there and if anything like what you need exists, they'll know.

---

### Post by mehersanjeev on 2013-02-22
try this 


REM  *****  BASIC  *****
Option Explicit

Sub Main
  Print getAmountInWords("999999999.99")
End Sub


'********************************************************************************************************
'Function Name      :   getAmountInWords
'Description        :   To convert the Amount value into words(formatted as "000000000.00")
'                       (Maximum allowed limit 999999999.99)
'Input Parameters   :   Amount
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getAmountInWords(strAmount As String) As String
    Dim strIntPart          As String
    Dim strDecPart          As String
    Dim strCroresPart       As String
    Dim strLakhsPart        As String
    Dim strThousandsPart    As String
    Dim strHundredsPart     As String
    Dim strTensPart         As String
    Dim strOnesPart         As String
    Dim strDecTensPart      As String
    Dim strDecOnesPart      As String
    Dim strAmtWords         As String
    Dim dblIntPart          As Double
    Dim intDecPart          As Integer
    Dim strDecWords         As String
    Dim iErr As Integer

    'handle for typemismatch error
    '??Err.Clear
    '??On Error Resume Next
    On Error Goto BadError
    strAmount = CDbl(strAmount)
    '??If Err.Number = "13" Then
    '??    getAmountInWords = ""
    '??    Exit Function
    '??End If
    '??Err.Clear
    strAmount = Format(Trim(strAmount), "000000000.00")

    'if the value is negative,zero above the limit then give error message
    If Val(strAmount) < 0 Then
        getAmountInWords = ""
        Exit Function
    ElseIf Val(strAmount) = 0 Then
        getAmountInWords = "Rupees Zero"
        Exit Function
    ElseIf Val(strAmount) > 999999999.99 Then
        getAmountInWords = ""
        Exit Function
    End If

    'store the integer and decimal parts separately
    strIntPart = Mid(strAmount, 1, 9)
    strDecPart = Mid(strAmount, 11, 2)

    'store the individual places in variables
    strCroresPart = Mid(strIntPart, 1, 2)
    strLakhsPart = Mid(strIntPart, 3, 2)
    strThousandsPart = Mid(strIntPart, 5, 2)
    strHundredsPart = Mid(strIntPart, 7, 1)
    strTensPart = Mid(strIntPart, 8, 1)
    strOnesPart = Mid(strIntPart, 9, 1)
    strDecTensPart = Mid(strDecPart, 1, 1)
    strDecOnesPart = Mid(strDecPart, 2, 1)

    strAmtWords = ""
    'To make the Crores Part
    If Val(strCroresPart) <> 0 Then
        strAmtWords = strAmtWords & getCroresPart(strCroresPart)
    End If

    'To make the Lakhs Part
    If Val(strLakhsPart) <> 0 Then
        strAmtWords = strAmtWords & getLakhsPart(strLakhsPart)
    End If

    'To make the Thousands Part
    If Val(strThousandsPart) <> 0 Then
        strAmtWords = strAmtWords & getThousandsPart(strThousandsPart)
    End If

    'To make the hundreds Part
    If Val(strHundredsPart) <> 0 Then
        strAmtWords = strAmtWords & getOnesColumn(Format(strHundredsPart, "00")) & " Hundred "
    End If

    'To make Tens and Ones part
    If Val(strTensPart & strOnesPart) <> 0 And Val(strAmount) > 100 Then
        strAmtWords = strAmtWords & "and " & getTensOnesPart(strAmount, strTensPart, strOnesPart)
    Else
        strAmtWords = strAmtWords & getTensOnesPart(strAmount, strTensPart, strOnesPart)
    End If

    strDecWords = ""
    'To make Tens and Ones part in the decimal part
    If Val(strDecTensPart & strDecOnesPart) <> 0 Then
        strDecWords = strDecWords & getTensOnesPart(Val(strAmount), strDecTensPart, strDecOnesPart)
    End If

    'If both integer and decimal part are not Zero then add Rupees and Paise only
    If Val(strDecPart) <> 0 And Val(strIntPart) <> 0 Then
        getAmountInWords = "Rupees " & strAmtWords & " and " & strDecWords & " Paise only"
    'If deciaml part is zero then add Rupees and only
    ElseIf Val(strIntPart) <> 0 And Val(strDecPart) = 0 Then
        getAmountInWords = "Rupees " & strAmtWords & " Only"
    'If Integer part is zero then add Paise only
    ElseIf Val(strIntPart) = 0 And Val(strDecPart) <> 0 Then
        getAmountInWords = strDecWords & " Paise Only"
    End If
    '??Replace is not supported in OOo Basic
    '??getAmountInWords = Trim(Replace(getAmountInWords, "  ", " "))
    getAmountInWords = Trim(getAmountInWords, "  ", " ")
    Exit Function
BadError:
   iErr = Err
   If Err = 13 Then
     getAmountInWords = ""
     Exit Function
   Else
     REM OK, do what?
     getAmountInWords = ""
     Print "Did not expect to get here with err " & iErr
   End If
End Function

'********************************************************************************************************
'Function Name      :   getOnesColumn
'Description        :   To convert the number in ones column into words
'Input Parameters   :   String(ones value formated as "00")
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getOnesColumn(strValue As String) As String
    Select Case strValue
        Case "01"
            getOnesColumn = "One"
        Case "02"
            getOnesColumn = "Two"
        Case "03"
            getOnesColumn = "Three"
        Case "04"
            getOnesColumn = "Four"
        Case "05"
            getOnesColumn = "Five"
        Case "06"
            getOnesColumn = "Six"
        Case "07"
            getOnesColumn = "Seven"
        Case "08"
            getOnesColumn = "Eight"
        Case "09"
            getOnesColumn = "Nine"
    End Select
End Function

'********************************************************************************************************
'Function Name      :   getTensColumnWithOne
'Description        :   To convert the number in tens and ones column into words
'                       if the combined(tens+ones) value is between 10 and 19
'Input Parameters   :   String
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getTensColumnWithOne(strValue As String) As String
    Select Case strValue
        Case "10"
            getTensColumnWithOne = "Ten"
        Case "11"
            getTensColumnWithOne = "Eleven"
        Case "12"
            getTensColumnWithOne = "Twelve"
        Case "13"
            getTensColumnWithOne = "Thirteen"
        Case "14"
            getTensColumnWithOne = "Fourteen"
        Case "15"
            getTensColumnWithOne = "Fifteen"
        Case "16"
            getTensColumnWithOne = "Sixteen"
        Case "17"
            getTensColumnWithOne = "Seventeen"
        Case "18"
            getTensColumnWithOne = "Eighteen"
        Case "19"
            getTensColumnWithOne = "Nineteen"
    End Select
End Function

'********************************************************************************************************
'Function Name      :   getTensColumn
'Description        :   To convert the number in tens column into words
'                       if the combined(tens+ones) value is between 20 and 99
'Input Parameters   :   String
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getTensColumn(strValue As String) As String
    Select Case strValue
        Case "2"
            getTensColumn = "Twenty"
        Case "3"
            getTensColumn = "Thirty"
        Case "4"
            getTensColumn = "Forty"
        Case "5"
            getTensColumn = "Fifty"
        Case "6"
            getTensColumn = "Sixty"
        Case "7"
            getTensColumn = "Seventy"
        Case "8"
            getTensColumn = "Eighty"
        Case "9"
            getTensColumn = "Ninety"
    End Select
End Function

'********************************************************************************************************
'Function Name      :   getCroresPart
'Description        :   To convert the crore part into words
'Input Parameters   :   String(crore value)
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getCroresPart(strCrore As String) As String
    If Val(strCrore) < 10 Then
        If Val(strCrore) = 1 Then
            getCroresPart = getOnesColumn(strCrore) & " Crore "
        Else
            getCroresPart = getOnesColumn(strCrore) & " Crores "
        End If
    ElseIf Val(strCrore) < 20 Then
        getCroresPart = getCroresPart & getTensColumnWithOne(strCrore) & " Crores "
    Else
        getCroresPart = getCroresPart & getTensColumn(Mid(strCrore, 1, 1))
        If Mid(strCrore, 2, 1) <> "0" Then
            getCroresPart = getCroresPart & " " & _
                            getOnesColumn(Format(Mid(strCrore, 2, 1), "00"))
        End If
        getCroresPart = getCroresPart & " Crores "
    End If
End Function

'********************************************************************************************************
'Function Name      :   getLakhsPart
'Description        :   To convert the lakh part into words
'Input Parameters   :   String(Lakh value)
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getLakhsPart(strLakh As String) As String
    If Val(strLakh) < 10 Then
        If Val(strLakh) = 1 Then
            getLakhsPart = getLakhsPart & getOnesColumn(strLakh) & " Lakh "
        Else
            getLakhsPart = getLakhsPart & getOnesColumn(strLakh) & " Lakhs "
        End If
    ElseIf Val(strLakh) < 20 Then
        getLakhsPart = getLakhsPart & getTensColumnWithOne(strLakh) & " Lakhs "
    Else
        getLakhsPart = getLakhsPart & getTensColumn(Mid(strLakh, 1, 1))
        If Mid(strLakh, 2, 1) <> "0" Then
            getLakhsPart = getLakhsPart & " " & _
                            getOnesColumn(Format(Mid(strLakh, 2, 1), "00"))
        End If
        getLakhsPart = getLakhsPart & " Lakhs "
    End If
End Function

'********************************************************************************************************
'Function Name      :   getThousandsPart
'Description        :   To convert the thousand part into words
'Input Parameters   :   String(thousand value)
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getThousandsPart(strThousand As String) As String
    If Val(strThousand) < 10 Then
        getThousandsPart = getThousandsPart & getOnesColumn(strThousand) & " Thousand "
    ElseIf Val(strThousand) < 20 Then
        getThousandsPart = getThousandsPart & getTensColumnWithOne(strThousand) & " Thousand "
    Else
        getThousandsPart = getThousandsPart & getTensColumn(Mid(strThousand, 1, 1))
        If Mid(strThousand, 2, 1) <> "0" Then
            getThousandsPart = getThousandsPart & " " & _
                            getOnesColumn(Format(Mid(strThousand, 2, 1), "00"))
        End If
        getThousandsPart = getThousandsPart & " Thousand "
    End If
End Function

'********************************************************************************************************
'Function Name      :   getTensOnesPart
'Description        :   To convert the tens and ones part into words
'Input Parameters   :   actual total amount,tens value,ones value
'Returns            :   String
'Creat by 			:  	Sanjeev Meher on 9th Feb 2013
'Specific Logic used:   None
'********************************************************************************************************
Public Function getTensOnesPart(strAmount As String, strTensPart As String, strOnesPart As String) As String
    If Val(strTensPart & strOnesPart) < 10 Then
        getTensOnesPart = getTensOnesPart & getOnesColumn(strTensPart & strOnesPart)
    ElseIf Val(strTensPart & strOnesPart) < 20 Then
        getTensOnesPart = getTensOnesPart & getTensColumnWithOne(strTensPart & strOnesPart)
    Else
        getTensOnesPart = getTensOnesPart & getTensColumn(strTensPart)
        If Mid(strOnesPart, 2, 1) <> "0" Then
            getTensOnesPart = getTensOnesPart & " " & getOnesColumn(Format(strOnesPart, "00"))
        End If
    End If
End Function

---

### Post by wildmanne39 on 2013-02-22
Old thread closed.

---

