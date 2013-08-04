RifflePDF
=========

RifflePDF is a script to collate pages in PDF to publish documents as a
compact brochure.

What is RifflePDF?
------------------

To bind a documents like a brochure, there is a method to print 4 pages on
both sides of a piece of paper as the following figure:

            /|  
        /| / |
       / |/ 5|
      / 7/___|____
     /___|____    |
    |         |   |
    |x        |3  | `x` represents the places to bind
    |    1    |   |
    |x        |___|
    |_________|

In the case of this way, you need to collate the pages .  For example, if
you will collate 8 pages p1,p2,...,p8, the pages are collated in the
following order: 8 1, 2, 7, 6, 3, 4, 5.

    [1][2][3][4][5][6][7][8] ---[collate]--> [8][1][2][7][6][3][4][5]
     _______  _______  _______  _______  
    |   :   ||   :   ||   :   ||   :   | 
    | 8 : 1 || 2 : 7 || 6 : 3 || 4 : 5 | 
    |___:___||___:___||___:___||___:___| 
      ---- in order --->

RifflePDF collates the pages in the PDF document as the above order with
one command on a terminal.  If the number of the pages is not multiples of
4, RifflePDF will insert the blank pages.

    [1][2][3][4][5][6] ---[collate]--> [ ][1][2][ ][6][3][4][5]
     _______  _______  _______  _______  
    |   :   ||   :   ||   :   ||   :   | 
    |   : 1 || 2 :   || 6 : 3 || 4 : 5 | 
    |___:___||___:___||___:___||___:___| 
      ---- in order --->


Usage
-----

To collate the pages in PDF, run a command:

    $ rifflepdf -o output.pdf input.pdf

then the collated PDF `output.pdf` will be generated.

RifflePDF uses the PDF processor pdftk or poppler command line tools as
the back-end.  RifflePDF detects the PDF processor and choose one
automatically.  If both processor is installed in your computer, RifflePDF
uses pdftk as default.  If you need to select yourself, use `-m` option:

    $ rifflepdf -o output.pdf -m pdftk input.pdf

Using pdftk is suggested, because the size of the collated file is huge,
and processing is not so fast.


Requirement
-----------

You need to install either pdftk or poppler command line tools.  Pdftk is
provided by package `pdftk`, and poppler utilities may be provided by
`poppler-utils` or `poppler-tools`.


License and Copyright 
---------------------

Copyright (c) 2013 Shin'ya Ueoka.
RifflePDF is licensed under MIT licence.

