---
title: "problem with pdfcrop - alternative?"
date: 2011-10-14
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-14
'pdfcrop' is a command line utility which crops off the white border around PDFs. But it doesn't work as it should. It seems to calculate the right "box" to crop out of the PDF, but this box is placed wrong. It only cuts the PDF from the left and bottom side, i.e. the box is placed in the top right of the PDF instead of in the middle. The resulting PDF still has white borders on the right and top sides, but text is cut off on the left and bottom side. 

Does anyone either know a solution to this problem or an alternative to pdfcrop? I've already done some googling but didn't find anything...

---

### Post by TeoBigusGeekus on 2011-10-14
If you don't find anything and you're not talking about a lot of pages, consider opening the document with gimp and croping the pages manually.
I know, I know...
...but if everything else fails, what are you gonna do?

---

### Post by CryptKeeper777 on 2011-10-14
> **TeoBigusGeekus said:**
> If you don't find anything and you're not talking about a lot of pages, consider opening the document with gimp and croping the pages manually.
I know, I know...
...but if everything else fails, what are you gonna do?
I am talking about a lot of pages... And not just a single PDF but I generally want to crop white space from PDFs, preferably automatically on command line.

---

### Post by CryptKeeper777 on 2011-10-14
I'll try it with other PDFs maybe it's the problem of the PDF rather than the script...

---

### Post by CryptKeeper777 on 2011-10-23
pdfcrop works fine, I had just bad luck with the PDF file. I wrote a short shell script which crops the PDF after it aked the user for margins, saves it in a temporary file, opens both the uncropped and the cropped PDFs for comparison, asks if the user's satisfied with the result and if not, crops the PDF again, once again asking for margins. 

The reason to use pdfcrop in the first place is that I want to optimize PDFs to read them on my Kindle eBook reader. The script crops the PDF trial-end-error-style as described above and resizes it, that is, prints the PDF in a custom paper format.

```

#!/bin/bash
#####################################################################
# usage: kindlepdf <pdffile.pdf>
#####################################################################
# Script to make PDFs Kindle-friendly, which means, cropping away
# the white border around the actual content of the PDF and then
# resizing the PDF to be 3.3" in width. The resulting PDF (ending
# on _kindle.pdf) can be isplayed on the 6" Kindle-display in
# portrait mode in "actual size"-zoom mode without content being
# cut off on the left or right side. This way one can read the PDF
# without the text line in the vertical center being half cut-off,
# as is the case when the PDF is displayed in landscape with "fit
# width"-zoom mode.
#####################################################################

pdf_precrop=$1
if [[ ! $1 ]]; then 
    echo "usage: kindlepdf <pdffile.pdf>" 
    exit
elif [[ ! -f "$1" ]]; then
    echo "$1 could not be opened. Please try again!"
    exit
fi

pdf_crop=".pdfcrop-tmp.pdf"

crop=false      # cropping successful or not
ans=false       # given answer valid or not
retry=false     # crop again of not
while [[ $crop == false ]]; do

    # let user enter margins for pdfcrop's --margin option
    echo -e "\nEnter margins for PDF white-border-cropping." 
    echo " -> format: left top right bottom"
    echo " -> standard: 0 0 0 0"
    echo -n " -> "
    read mrgns

    if [[ ! $mrgns ]]; then mrgns="0 0 0 0"; fi

### CHECK IF THE INPUT IS OF THE RIGHT FORMAT ###


    echo -e "\nCropping $pdf_precrop."
    pdfcrop --margins "$mrgns" "$pdf_precrop" "$pdf_crop" >/dev/null

    echo -e "\nOpen original and cropped PDFs for comparison."
    
    # open original and cropped PDFs to check if looks good
    xdg-open $pdf_precrop &>/dev/null
    xdg-open $pdf_crop &>/dev/null
    
    # ask the user if the cropped PDF looks good
    ans=false
    while [[ $ans == false ]]; do
        echo -en "\nSatisfied with the result (y/n)? " 
        read reply
        if [[ $reply == "Y" ]] || 
           [[ $reply == "y" ]] 
        then # PDF looks good, go on
            echo -e "\nCropping $pdf_precrop successful!"
            ans=true # valid answer given
            crop=true # cropping successful
            #break # jump out of loop
        elif [[ $reply == "N" ]] || 
             [[ $reply == "n" ]]
        then # PDF doesn't look good...
            ans=true # valid answer given
            echo -e "\nTry it again using differeng margins!"
        else # stupid user needs another try...
            echo "Invalid answer. Try again!"
        fi
    done
    echo -e "\n----------------------------------------"
done

#####################################################################

# 1 inch = 72 points --> 3.3 inch = 237.6 points ~ 240 points
#                    --> 4.6 inch = 331.2 points ~ 330 points

echo -e "\nResizing cropped PDF to Kindle-friendly format."

w_out=320 # width of output PDF [points]
#w_out=230

pdf_in=$pdf_crop
pdf_in_name=${pdf_precrop:0:${#pdf_precrop}-4}

if [ ! $2 ]; then pdf_out="$pdf_in_name""_kindle.pdf";
             else pdf_out=$2; fi

w_in=$(identify -format "%w\n" $pdf_in | head -2 | tail -1) # PDF width [px]
h_in=$(identify -format "%h\n" $pdf_in | head -2 | tail -1) # PDF height [px]

h_w_ratio=$(( 100 * h_in / w_in )) # height/width [%]
h_out=$(( h_w_ratio * w_out / 100 )) # height of putput PDF [points]

#gs -q \
#   -sOutputFile="$pdf_out" \
#   -sDEVICE=pdfwrite \
#   -dNOPAUSE \

#   "$pdf_in"

echo ""
echo "in: $w_in x $h_in px" 
echo "out: " \
     "$(( $w_out/72 )).$(( 10*$w_out/72 - 10*($w_out/72) )) x" \
     "$(( $h_out/72 )).$(( 10*$h_out/72 - 10*($h_out/72) )) inch" \
     "= $w_out x $h_out pt"
echo ""

# print $pdf_in in Kindle-format as $pdf_out
gs -q \
   -dPDFFitPage \
   -sOutputFile="$pdf_out" \
   -sDEVICE=pdfwrite \
   -dDEVICEWIDTHPOINTS=$w_out \
   -dDEVICEHEIGHTPOINTS=$h_out \
   -dFIXEDMEDIA \
   -dNOPAUSE \
   -dBATCH \
   "$pdf_in"

echo "Opening generated file:"
ls "$pdf_out"
xdg-open "$pdf_out" &>/dev/null # open generated Kindle-friendly PDF

rm $pdf_crop # cleaning up

echo -e "\n----------------------------------------"

#####################################################################

```

---

### Post by techvish81 on 2011-10-23
install gscan2pdf and import pdf file in it , mess with the cleanup , unpaper option and u will what u want .

---

