# OpenPDF Cheatsheet
The first time I had to create PDFs for a customer project (20 years ago, ouch :-O ), I was using iText which was the state of 
the art library in Java. Bruno Lowagie - who developed iText - has always been helpful answering all my dumb questions. Due 
to a [dispute with the belgium government](https://techcrunch.com/2009/05/20/open-source-developer-intends-to-block-belgian-government-from-using-his-technology-over-tax-dispute/)
he changed his license for commercial usage. 

One of the sole alternatives was [pdfbox](https://pdfbox.apache.org/) which is
perfect for low level construction of PDFs...what's missing is the high level API iText was providing. So in 2012 I started
[a bunch of functions for formatting and layouting](https://github.com/ralfstuckert/pdfbox-layout) to solve this problem in 
a customer project at this time. Alas, the streaming approach was not suitable for recursive layouts, so I dropped support for that. 

Recently I had to create PDF again for customer project and I refused to use the low level pdfbox stuff, so I was looking for a lib that
would do the job. I knew that iText 4 - the last free version - had been forked quite a while ago as [OpenPDF](https://github.com/LibrePDF/OpenPDF), 
so I gave it a try. I still love iText's easy high level approach, but the documentation of the project is... eh, not as 
perfect as it was for iText. So I was plowing through the examples and made some notes, to get some kind of index of most 
common use cases, and here my notes with some sample PDFs.

## Document
* [Landscape/Portrait](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/LandscapePortrait.java) [![PDF](icons/icons8-pdf-32.png)](pdf/LandscapePortrait.pdf)
* [Margins](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/Margins.java) [![PDF](icons/icons8-pdf-32.png)](pdf/Margins.pdf)
* [Page Size](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/DefaultPageSize.java) [![PDF](icons/icons8-pdf-32.png)](pdf/DefaultPageSize.pdf)

## Paragraphs, Chunks
Chunks are the smallest units for text with a given font, color etc. Paragraphs are containers for elements like chunks, images etc.
* [Paragraphs](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/Paragraphs.java) [![PDF](icons/icons8-pdf-32.png)](pdf/Paragraphs.pdf)
* [Chunks](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/Chunks.java) [![PDF](icons/icons8-pdf-32.png)](pdf/Chunks.pdf)

## Lists
* [Lists](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/Lists.java) [![PDF](icons/icons8-pdf-32.png)](pdf/lists.pdf)

## Tables
* [Tables](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/tables/MyFirstTable.java) [![PDF](icons/icons8-pdf-32.png)](pdf/MyFirstTable.pdf)

Find many more examples demonstating padding, borders, colors, images, nested Tables in the [same package](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/tables)

## Images
* [Images](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/images/Images.java) [![PDF](icons/icons8-pdf-32.png)](pdf/Images.pdf)

* Find many more examples demonstating transformation, filter, alignment, etc in the [same package](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/images)

## Column Layout
Allows you to organize content in columns like in a newspaper or a table
* [Column Layout](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/columns/ColumnSimple.java) [![PDF](icons/icons8-pdf-32.png)](pdf/columnsimple.pdf)

## Links
* [Links](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/objects/anchors/AHref.java) [![PDF](icons/icons8-pdf-32.png)](pdf/AHref.pdf)

## concatenate PDFs
* [Concat multiple PDF](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/tools/ConcatPdfTest.java) [![PDF](icons/icons8-pdf-32.png)](pdf/concat2.pdf)
* [Import pages from another PDF](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/copystamp/TwoOnOne.java) [![PDF](icons/icons8-pdf-32.png)](pdf/2on1.pdf)

## Watermark
* [Add a watermark](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/toolbox/plugins/watermarker/WatermarkerTest.java) [![PDF](icons/icons8-pdf-32.png)](pdf/Result.pdf)
* [Watermark an existing PDF](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/copystamp/AddWatermarkPageNumbers.java) [![PDF](icons/icons8-pdf-32.png)](pdf/watermark_pagenumbers.pdf)


## Encryption
encrypt
* [Password encrypt](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/HelloEncrypted.java) [![PDF](icons/icons8-pdf-32.png)](pdf/HelloEncrypted.pdf)
* [Read encrypted PDF](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/read/ReadEncrypted.java) [![PDF](icons/icons8-pdf-32.png)](pdf/HelloEncrypted.pdf)
* [Encrypt existing PDF](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/general/copystamp/EncryptorExample.java) [![PDF](icons/icons8-pdf-32.png)](pdf/encrypted.pdf)

Be aware that you need to add bouncycastle for encryption
```xml
        <dependency>
            <groupId>org.bouncycastle</groupId>
            <artifactId>bcprov-jdk18on</artifactId>
        </dependency>
        <dependency>
            <groupId>org.bouncycastle</groupId>
            <artifactId>bcpkix-jdk18on</artifactId>
        </dependency>
```

## Forms
* [Create Form](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/forms/SimpleRegistrationForm.java) [![PDF](icons/icons8-pdf-32.png)](pdf/SimpleRegistrationForm.pdf)
* [Fill a form](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/forms/fill/Register.java) [![PDF](icons/icons8-pdf-32.png)](pdf/registered.pdf)

Find many more examples demonstating buttons, combos, etc in the [same package](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/forms)

## PDFA
* [Create PDF/A](https://github.com/LibrePDF/OpenPDF/blob/master/pdf-toolbox/src/test/java/com/lowagie/examples/conformance/PdfA1B.java) [![PDF](icons/icons8-pdf-32.png)](pdf/PdfA1B.pdf)
* [Validate PDF/A](https://github.com/LibrePDF/OpenPDF/blob/master/openpdf/src/test/java/com/lowagie/text/validation/PDFValidationTest.java) 



Icons by [Icon8](https://icons8.com/)