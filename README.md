## Some useful tools
1. 收尋字串 "pico"  
  $grep pico text.txt
2. 將結果輸出到某個檔案  
  $./abc>text.txt
3. 把亂把變成可讀字串(可搭配1.2.)  
  $strings text  
4. 解讀執行檔等檔案([readelf_and_objdump介紹](./Knowledges/readelf_and_objdump.md))  
  $readelf -s 123  
5. 得到每個段的大小、資料、存放位置、反解譯([readelf_and_objdump介紹](./Knowledges/readelf_and_objdump.md))  
  $objdump -x -s -d 123(.o)  

## pwn
### buffer overflow 1
使用工具: <b>$readelf</b>, 也可以用objdump等工具  
解決方法: 找出win的位置，透過overflow，將return address複寫成win的位置  
參考網站: [picoctf-2018-writeup](https://github.com/PlatyPew/picoctf-2018-writeup/tree/master/Binary%20Exploitation/buffer%20overflow%201)  
### buffer overflow 解法  
1. 找到變數位置  
  (gdb) p &a  
2. 找到stack底位置  
  (gdb) p $rbp  
3. 找到要跳去的function位置  
  (gdb) p function  
4. 如果變數位置為0x7fffffffe100，rbp位置為0x7fffffffe120，則  
  需先隨便輸入比如'A'\*32個之後輸入function的位置，注意是little還是big endian，還有16進位的輸入問題(可借助python)。參考網站: [picoctf-2018-writeup](https://github.com/PlatyPew/picoctf-2018-writeup/tree/master/Binary%20Exploitation/buffer%20overflow%201) 
