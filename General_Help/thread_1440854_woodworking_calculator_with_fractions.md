---
title: "woodworking calculator with fractions?"
date: 2010-03-28
forum: General Help
---

### Post by rebeltaz on 2010-03-28
Is there any Linux calculator that can add, multiply, divide and subtract fractions, even if they have different denominators? 

When I need to divide 31 11/16 in half, for instance, I am having to first convert 11/16 to a decimal (.6875), add that to the 31 (31.6875) and then divide that in half (15.84375). Then I have to try and figure out what in the world the fractional equivalent of that decimal (.84375) is! Luckily, I was able to find a web site that has a chart with the most common woodworking denominators up to 64ths. The answer, BTW, is 15 27/32.

But that isn't the point. Going through all of those steps seems like an awful waste of computing power to me. Isn't that why computers where invented after all, to simply math?

The Linux version of [this]("http://www.calculated.com/prd286/Construction+Master+Pro+for+Windows.html") would be fantastic!

---

### Post by jerrrys on 2010-03-28
don't have an answer for you, but this may help your search

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+calculator+with+fractions&as_qdr=all&sa=Google+Search&lang=en#932](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=+calculator+with+fractions&as_qdr=all&sa=Google+Search&lang=en#932)

---

### Post by HermanAB on 2010-03-28
Hmm, you can probably do it with calc, but you'll have to read the manual!

Here is a calculator that may work on Wine:
[http://www.cab-tech.com/programs/cccalc.exe](http://www.cab-tech.com/programs/cccalc.exe)

---

### Post by Directive 4 on 2010-03-28
don't know about calc's but you don't have to convert to decimal


31 11/16                                     ..................................with                                                        (31 * 16 = 496)  ( + 11)

= 507/16

divide by 2 

= 507/32

(with 15 * 32 = 480) and ( 480 - 507 = 27)


hence 507/32 

= 480/32 + 27/32

= 15 27/32

---

### Post by falconindy on 2010-03-28
There's a far simpler method...

31 11/16 is the same as 30 27/16, which is easy to divide by 2.

Given that woodworking is always "neat" fractions, you can usually do this stuff on paper with a little ingenuity.

---

### Post by Zill on 2010-03-28
rebeltaz:  You could just use a cheap pocket calculator that works with fractions such as the [Casio FX85ES]("http://www.casio.co.uk/Products/Calculators/Scientific%20Calculators/FX-85ES-S-UH/Technical_Specifications/").

Alternatively, for a Linux solution, a simple spreadsheet (Gnumeric or openoffice.org Calc) should suffice.

---

### Post by gmargo on 2010-03-28
Here's one way to do your example calculation with "calc" (from the **apcalc** package):

```

$ calc
C-style arbitrary precision calculator (version 2.12.1.13)
Calc is open software. For license details type:  help copyright
[Type "exit" to exit, or "help" for help.]

; config("mode","frac")
        "real"
; a = 31 + 11/16
; a = a/2
; print int(a),frac(a)
15 27/32

```

---

### Post by underquark on 2010-03-28
OMG, are millimetres really that abhorrent?  I know that 2x4 and 4x4 and 1x2 are very good, anthropometric, measures and I still ask for lumber that way sometimes but when it comes to designing and building things (I have to admit that I use Sketchup under Windows) then millimetres really are so much easier to work with.

Having said that, OO Calc goes down to 64ths without any problem and smaller than that you're talking about sandpapering.

---

### Post by roger_1960 on 2010-03-28
Hi

If you have the "construction master pro software, have you tried running it with WINE?

---

### Post by rebeltaz on 2010-03-28
> **underquark said:**
> OMG, are millimetres really that abhorrent?  I know that 2x4 and 4x4 and 1x2 are very good, anthropometric, measures and I still ask for lumber that way sometimes but when it comes to designing and building things (I have to admit that I use Sketchup under Windows) then millimetres really are so much easier to work with.

Dude, when I am doing my own projects that I design, I can assure you that I am a firm believer in the metric system. I prefer a simple base-10 system to a we-just-want-to-be-different arbitrary system. Problem is some of what I do is working with plans drawn by other people. Besides that, all of my tape measures are marked in inches and feet. 

> **roger_1960 said:**
> If you have the "construction master pro software, have you tried running it with WINE?

I may try that... Right now I am thinking about getting Construction Master to run on my PPC.

> **Zill said:**
> rebeltaz:  You could just use a cheap pocket calculator that works with fractions such as the [Casio FX85ES]("http://www.casio.co.uk/Products/Calculators/Scientific%20Calculators/FX-85ES-S-UH/Technical_Specifications/").

I have been looking at the ProjectCalc. I'll take a look at the Casio in a bit...

I appreciate all of your responses.

---

### Post by rebeltaz on 2010-03-29
I installed Construction Master on my PPC and I am in heaven! Thanks again...

---

### Post by spibou on 2010-04-05
Although the original poster has solved his problem I thought that this is an interesting programming exercise so I wrote a programme to do calculations with mixed fractions. The language is Common Lisp partly because I'm learning it and the practice will do me good and partly because it has out of the box some of the desired functionality.

```

; Written in April 2010 by Spiros Bousbouras.
; You can do whatever you want with this code.

(declaim (optimize (safety 3)))

(defstruct token
    (start 0 :type fixnum) ; This is the position inside the line the user typed
                           ; where the token starts
    (end 0 :type fixnum)
    (value nil :type (or integer rational function null))
    (kind 'whatever :type symbol))

(defun calculate-fraction
    (s &aux
           (tokens-number 0)
           (length-s (length s))
           (tokens-array (make-sequence 'vector length-s))
           (parse-position 0))
    (declare
        (ftype (function (string) (or rational integer null)) calculate-fraction)
        (type fixnum parse-position))
 "s contains the line to be parsed.The function returns nil on error otherwise the
  result of the calculation.In the case of error it also prints an error message."
    (when (eql 0 length-s) (return-from calculate-fraction 0))
    (labels (
           (digitp (c)
             "Checks whether c is a (decimal) digit or not.Unlike the standard
              DIGIT-CHAR-P the argument doesn't have to be a character."
              (and (characterp c) (digit-char-p c)))
           (get-char (m)
             "Returns the character on position m of s .If m is outside the array
              bounds nil is returned."
              (if (< -1 m length-s)
                  (aref s m)
                  nil))
           (add-token (start end value kind)
              (setf (aref tokens-array tokens-number)
                 (make-token :start start
                             :end end
                             :value value
                             :kind kind))
              (incf tokens-number))
           (get-start (position)
               (token-start (aref tokens-array position)))
           (get-end (position)
               (token-end (aref tokens-array position)))
           (get-value (position)
               (token-value (aref tokens-array position)))
           (get-kind (position)
               (token-kind (aref tokens-array position)))
           (move-array (i j)
             "Moves the part of tokens-array starting at position j to the part starting
              at position i .It must be (<= i j) .It also modifies the value of
              tokens-number so that it correctly reflects the new length of tokens-array"
              (setf (subseq tokens-array i) (subseq tokens-array j))
              (decf tokens-number (- j i))
              (setq tokens-array (subseq tokens-array 0 tokens-number)))
           (highlight-error (i j)
             "It is called when an error has been found.It prints the input line i.e. s,
              with the part which caused the error between triple exclamation marks.
              The error starts at position i and ends at position j."
              (format t "~A !!!~A!!! ~A~%"
                 (subseq s 0 i)
                 (subseq s i (1+ j))
                 (subseq s (1+ j))))
           (parse-error (i j)
              (format t "Parse error~%")
              (highlight-error i j)
              (return-from calculate-fraction nil))
           (parse-number
              (&aux n1 n2 e (m parse-position) c)
             "Should be called when parse-position points to a digit inside s.
              It decides whether the number is a fraction or an integer and adds the
              appropriate token(s) to tokens-array."
              (loop
                 (incf m)
                 (setq c (get-char m))
                 (unless (digitp c) (return))) ; This exits the loop , not the function !
              (setq n1 (parse-integer
                          (subseq s parse-position m)))
              (when (eql c #\/)
              ; The / perhaps indicates division or perhaps it's between the numerator and
              ; denominator of a fraction.The test in the next line will decide which of
              ; the two.
                 (when (digitp (get-char (1+ m)))
                 ; We have encountered a fraction i.e. a substring which looks like n1/n2
                 ; where n1 and n2 are sequences of decimal digits.
                    (setq e (+ 2 m))
                    (loop
                       (setq c (get-char e))
                       (unless (digitp c) (return))
                       (incf e))
                    (setq n2 (parse-integer
                          (subseq s (1+ m) e)))
                    (when (eql n2 0)
                       (format t "Fraction denominator was zero~%")
                       (highlight-error (1+ m) (1- e))
                       (return-from calculate-fraction nil))
                    (add-token parse-position (1- e) (/ n1 n2) 'fraction)
; Even if n2 divides n1 we still want entry 'fraction rather than 'integer because
; otherwise check-tokens  would reject things like   1 4/2
                    (setq parse-position e)
                    (return-from parse-number))
                 ; The / indicated division
                 (add-token parse-position (1- m) n1 'integer)
                 (add-token m m (function /) 'operation)
                 (setq parse-position (1+ m))
                 (return-from parse-number))
              ; There was no / right after n1
              (add-token parse-position (1- m) n1 'integer)
              (setq parse-position m))
           (tokenise (&aux c)
              (loop
                 (when (>= parse-position length-s)
                    (return-from tokenise))
                 (setq c (get-char parse-position))
                 (cond
                    ((or (eql c #\Space)
                         (eql c (name-char "tab")))
                       (incf parse-position))
                    ((eql c #\+)
                        (add-token parse-position parse-position
                                   (function +) 'operation)
                        (incf parse-position))
                    ((eql c #\-)
                        (add-token parse-position parse-position
                                   (function -) 'operation)
                        (incf parse-position))
                    ((eql c #\*)
                        (add-token parse-position parse-position
                                   (function *) 'operation)
                        (incf parse-position))
                    ((eql c #\/)
                        (add-token parse-position parse-position
                                   (function /) 'operation)
                        (incf parse-position))
                    ((eql c #\( )
                        (add-token parse-position parse-position
                                   nil 'left-par)
                        (incf parse-position))
                    ((eql c #\) )
                        (add-token parse-position parse-position
                                   nil 'right-par)
                        (incf parse-position))
                    ((digitp c) (parse-number))
                    (t (format t "Unknown input character~%")
                       (highlight-error parse-position parse-position)
                       (return-from calculate-fraction nil)))))
           (check-tokens (&aux k1 k2 i)
             "Checks that certain tokens do not appear in places they shouldn't and
              that certain illegal combinations of tokens do not appear.The function
              must only be called if there is at least 1 token."
              (when (position (get-kind 0) '(operation right-par))
                 (parse-error (get-start 0) (get-end 0)))
              (setq i (1- tokens-number))
              (when (position (get-kind i) '(operation left-par))
                 (parse-error (get-start i) (get-end i)))
              (dotimes (i (1- tokens-number))
                 (setq k1 (get-kind i) k2 (get-kind (1+ i)))
                 (when (or
                          (and
                             (eql k1 'operation)
                             (position k2 '(operation right-par)))
                          (and
                             (eql k1 'integer)
                             (position k2 '(integer left-par)))
                          (and
                             (eql k1 'fraction)
                             (position k2 '(fraction integer left-par)))
                          (and
                             (eql k1 'left-par)
                             (position k2 '(right-par operation)))
                          ; For simplicity we're not allowing for example "(-5)"
                          ; One could write instead "(0-5)"
                          (and
                             (eql k1 'right-par)
                             (position k2 '(left-par fraction integer))))
                    (parse-error (get-start i) (get-end (1+ i))))))

           (check-div-by-0 (p1 p2)
             "Verifies that there is no division by zero between positions p1 and p2
              inclusive.It is assumed that within this range there are no parentheses
              and that on positions p1 and p2 there are numbers."
              (declare (type (and fixnum (integer 0)) p1 p2))
              (do   ((i (1+ p1) (+ 2 i)))
                   ((>= i p2))
                 (when (eql (get-value i) (function /))
                    (when (eql (get-value (1+ i)) 0)
                       (format t "Division by zero~%")
                       (highlight-error (get-start i) (get-end (1+ i)))
                       (return-from calculate-fraction nil)))))

           (eliminate-mixed-fractions (&aux (i 0) old s)
             "Replaces something like '1 1/2' with '3/2' "
              (loop
                 (setq old tokens-number)
                 (loop
                    (when (>= i (1- tokens-number))
                       (return))
                    (when (and (eql (get-kind i) 'integer)
                               (eql (get-kind (1+ i)) 'fraction))
                       (setq s (make-token
                                  :start (get-start i)
                                  :end (get-end (1+ i))
                                  :value (+ (get-value i) (get-value (1+ i)))
                                  :kind 'fraction))
                       (setf (aref tokens-array i) s)
                       (move-array (1+ i) (+ 2 i))
                       (incf i)
                       (return))
                    (incf i))
                 (when (eql old tokens-number)
                    (dotimes (j tokens-number)
                       (when (eql (get-kind j) 'integer)
                          (setf (token-kind (aref tokens-array j))
                             'fraction)))
                    (return-from eliminate-mixed-fractions))))

           (eliminate-operations (p1 p2)
             "p1 and p2 are positions spanning a range of tokens which has only
              numbers and operations , on positions p1 and p2 there are numbers
              and no range properly containing [p1,p2] satisfies the same properties.
              The function performs the operations in the specified range taking
              care to place priority on multiplication/division vs
              addition/subtraction."
              (declare (type (and fixnum (integer 0)) p1 p2))
              (flet
                   ((eliminate-op-aux (op1 op2 &aux op s old)
                      (loop
                         (setq old tokens-number)
                         (do   ((i (1+ p1) (+ 2 i)))
                              ((>= i p2))
                           (setq op (get-value i))
                           (when (or (eql op op1) (eql op op2))
                              (setq s (make-token
                                  :start (get-start (1- i))
                                  :end (get-end (1+ i))
                                  :value (funcall
                                            op (get-value (1- i)) (get-value (1+ i)))
                                  :kind 'fraction))
                              (setf (aref tokens-array (1- i)) s)
                              (move-array i (+ 2 i))
                              (decf p2 2)
                              (return)))
                         (when (eql old tokens-number)
                            (return-from eliminate-op-aux)))))
                 (check-div-by-0 p1 p2)
                 (eliminate-op-aux (function *) (function /))
                 (eliminate-op-aux (function +) (function -))))

           (eliminate-parentheses (&aux b e)
              (flet ((find-left-par ()
                        (do  ((i (1- tokens-number) (1- i)))
                            ((eql -1 i) (return-from find-left-par nil))
                          (when (eql 'left-par (get-kind i))
                             (return-from find-left-par i))))
                     (find-right-par (pos)
                        (do  ((i pos (1+ i)))
                            ((eql i tokens-number) (return-from find-right-par nil))
                          (when (eql 'right-par (get-kind i))
                             (return-from find-right-par i)))))
                 (loop
                    (setq b (find-left-par))
                    (unless b
                       (setq e (find-right-par 0))
                       (when e
                          (format t "Unmatched right parenthesis~%")
                          (highlight-error (get-start e) (get-end e))
                          (return-from calculate-fraction nil))
                       (return-from eliminate-parentheses))
                    (setq e (find-right-par (1+ b)))
                    (unless e
                       (format t "Unmatched left parenthesis~%")
                       (highlight-error (get-start b) (get-end b))
                       (return-from calculate-fraction nil))
                    (when (< (1+ b) (1- e))
                       (eliminate-operations (1+ b) (1- e)))
                    (setf (aref tokens-array b)
                       (make-token :start (get-start b)
                                   :end (get-end (+ 2 b))
                                   :value (get-value (1+ b))
                                   :kind 'fraction))
                    (move-array (1+ b) (+ 3 b))))))
; Local function definitions finish here

       (tokenise)
       (when (eql 0 tokens-number) (return-from calculate-fraction 0))
       (check-tokens)
       (eliminate-mixed-fractions)
       (eliminate-parentheses)
       (when (> tokens-number 1)
          (eliminate-operations 0 (1- tokens-number)))
       (get-value 0)))


(defun read-and-print (&aux s r i f)
   (loop
      (setq s (read-line *standard-input* nil))
      (unless s (return))
      (setq r (calculate-fraction s))
      (when r
         (cond ((integerp r) (format t "~A~%" r))
               ((> r 0) (multiple-value-setq (i f) (floor r))
                        (format t "~A ~A~%" i f))
               (t  (multiple-value-setq (i f) (floor (- r)))
                   (format t "-(~A ~A)~%" i f))))))

(read-and-print)

```

You need to save it under some file name , let's say ~/fractions .In order to run it you obviously need a Common Lisp compiler. I only used the standard parts of the language so any conforming compiler will do but since I used SBCL to test it you may as well try that.```
sudo apt-get sbcl
```
Now you do```
sbcl --script ~/fractions
```and  you can start typing your calculations.```
31 11/16/2
15 27/32

```
In order to exit you need to press control-d on an empty line. (For reasons having to do with SBCL and outside the control of the programme you may need to press control-d twice to go back to the shell command line.)

The programme supports addition , subtraction , multiplication and division. As usual multiplication and division take priority over addition and subtraction but you can use parentheses if you want to change priorities. For example```

5 1/2 + 7 8/9 * 23 5/2
206 2/3
(5 1/2 + 7 8/9) * 23 5/2
341 5/12

```
A feature I especially like is that if there is division by zero the programme will actually tell you which subexpression caused the problem. For example```

(12+3)/(5-9) + 7/(3 1/4 - 5 - 10 11/12 + 5 3/7*2 1/3) + 5 /14
Division by zero
(12+3)/(5-9) + 7 !!!/(3 1/4 - 5 - 10 11/12 + 5 3/7*2 1/3)!!!  + 5 /14

```
It tells you that the expression```

(3 1/4 - 5 - 10 11/12 + 5 3/7*2 1/3)
```
is zero.

---

### Post by maximzavadskiy on 2011-09-27
Hi guys! I know the solution - Visual ExpressionCalculator([http://visualexpcalc.sourceforge.net/](http://visualexpcalc.sourceforge.net/)). It cross-platform intuitive fraction and mixed number calculator. By the way - I'm the developer of it;)
Enjoy it!:popcorn:

---

