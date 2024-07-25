ขั้นตอน Golang
1.download golang, พร้องติดตั้งที่เครือง      - mkdr ชื่อ folder 
2. สร้าง go module  พิมพ์คำสั่ง go mod init {{ชื่อ module}}
3. สร้าง file main ขึ้นมาเพื่อเขียน code  main.go
4. ติดตั้ง extension => Go , Error Lens, Code Runner
5. วิธี run:  go run program.go


เป็นคำสั่งเพื่อบอกว่าเมื่อ run จะให้เริ่มต้นทำงานที่ package นี้เป็นอันดับแรก
ถ้า import เข้ามาแล้วไม่ใช่จะ error fmt มากับภาษา go อยู่แล้วไม่ต้องติดตั้งเพิ่มเอาไว้แสดงผล รวมเครื่องจัด input output
ไม่ต้องใส่ ; เพื่อปิดประโยคก็ได้
---------------------------------------------------------------------------
data type
ิbool                            ค่าเริ่มต้น false
int                             ค่าเริ่มต้น 0
float32  float64  เลขจุดทศนิยม    ค่าเริ่มต้น 0
string ชุดข้อความ                 ค่าเริ่มต้น ""

นิยามตัวแปล
1. ประกาศตัวแปลพร้อมชนิดข้อมูล  var name string
2. ประกาศตัวแปลโดยไม่ระบุชนิดข้อมูล  name := "ข้อมุล"
3. สร้างตัวแปลหลายตัว  var number1, number2= 10 , 3  หรือ number1, number2 := 10 , 3 

ค่าคงที่(Constant) ค่าที่ไม่สามารถเปลี่ยนแปลงได้

สัญญาลักษณ์ ตัวดำเนินการทางคณิตศาสตร์
บวก + 
ลบ -
คูณ *
หาร /
หารเอาเศษ %

การเปรียบเทียบ
เท่ากับ ==
ไม่เท่ากับ !=
มากกว่า >
น้อยกว่า <
มากกว่าเท่ากับ >=
น้อบกว่าเท่ากับ <=
---------------------------------------------------------------------------
การแสดงผล
1. Println ขึ้นบรรทัดใหม่      fmt.Println("My Name is ",name)
2. Printf ต่อประโยค     
%v  บอก value    fmt.Printf("Value is %v\n", name) 
%T บอก type       fmt.Printf("Type is %t", name)
\n ขึ้นบรรทัดใหม่

การรับค่า Scanf
fmt.Scanf(ประเภทข้อมูล, &ตัวแปร)  ex. fmt.Scanf("%s", &name)

Sring Format
string          %s
Integer         %d
floating point  %f
---------------------------------------------------------------------------

switch case  ไม่ต้องใส่ break; แล้ว
	switch score {
		case 1 : name = "มีค่า 1"
		case 2 : name = "มีค่า 2"
		case 3 : fmt.Println("มีค่า 3")
	}

excemple program
func main(){
	var name string
	fmt.Printf("ป้อนชื่อ =")
	fmt.Scanf("%s", &name)
	fmt.Println(name)
}


func main(){
	var name string = "Tasanaporn"
	// var age int = 25
	// var score float32 = 99.99999
	// status := true
	number1, number2 := 10 , 3 
	
	fmt.Println("เท่ากันหรือไม่", number1 >= number2)
	fmt.Println("ผลบวก = ",number1 + number2)
	fmt.Println("ผลลบ = ", number1 - number2)
	fmt.Println("ผลคูณ = ", number1 * number2)
	fmt.Println("ผลหาร = ", number1 / number2)
	fmt.Println("ผลเศษ = ", number1 % number2)
	fmt.Println("My Name is ",name)
	fmt.Printf("Value is %v", name)
	fmt.Printf("Type is %T", name)
	// fmt.Println("Age =", age)
	// fmt.Println("Score =", score)
	// fmt.Println("สอบผ่านไหม", status)
}
---------------------------------------------------------------------------

array
เริ่มต้นตำแหน่งที่ 0
ชนิดข้อมูลภายในต้องเป็นชนิดเดียวกัน
ไม่สามารถปรับเปลี่ยนขนาดได้
len() หาจำนวนข้อมูลว่ามีเท่าไหร่
numbers[{จำนวนข้อมูล}]{ชนิดข้อมูล}  
จำนวนข้อมูลใส่เป็นตัวเลขเพื่อจำกัดขนาด ถ้าไม่จำกัดให้ใส่ ... numbers[...]int 
เพิ่มข้อมูล numbers[1] = 500
ตัวอย่าง => var numbers[3]int  หรือ  numbers := [3]int{}
			var numbers[3]int = [3]int{100,200,300}
			numbers := [3]int{100,200,300}
---------------------------------------------------------------------------

Slices
คล้ายๆ array จะไม่มีการระบุขนาด names :=[] strung{}
เพิ่มข้อมูล  names = append(names,"สมหญิง")
เรียกใช้ข้อมูล names[0]
เรียกใช้ข้อมูลแบบกำหนดช่วง names[low:high]   =>  names[1:] 1 ถึงสุดท้าย
										=>  names[:2] 0 ถึง 1   ตำแหน่งสุดท้าย +1
										=> names[:] ทั้งหมด
func main(){
	numbers := [...]int{100,200,300}
	numbers[1] = 500

	names := []string{"สม","มานี"}
	names[1] = "tt"
	names = append(names, "ทดสอบ")
	fmt.Println(names[:2], len(names))
	fmt.Println(numbers[2], len(numbers))
}
---------------------------------------------------------------------------

Maps
ทราบ key เข้าถึง value ได้
var ชื่อตัวแปล map[key_type]value_type  => var country map[string]string{}
population := map[string]int{"England": 500}
population["Thai"] = 200
population["Japan"] = 100

func main(){
	country := map[string]string{"eg": "England"}
	country["th"] = "Thai"
	country["jp"] = "Japan"

	//ตรวจสอบข้อมูล
	value, check := country["jp"]
	if check {
		fmt.Println(value)
	}
	fmt.Println(country["eg"])
}
---------------------------------------------------------------------------

for loop
++ เพิ่มค่า -- ลดค่า
for ===>
for ค่าเริ่มต้นของตัวแปล; เงื่อนไข; เปลี่ยนแปลงค่าตัวแปล{
	fmt.println("Hollo Go programming")
}

for count := 1; count <= 3; count++ {
	fmt.println("Hollo Go programming")
}

for range ===>
for index, value := range number {
	fmt.Println(index, value)
}

ex program ===>
func main(){
	number := []int{10,20,30,40,50}
	for count := 0; count < len(number); count++ {
		if number[count] == 30 {
			continue
		}
		fmt.Println(number[count])
	}

	for count := 1; count <=3; count++{
		if count == 2 {
			break   //หยุดการทำงานเลย
			continue //ข้ามการทำงานเมื่อเข้าเงื่อนไขและทำงานต่อรอบต่อไป
		}
		fmt.Println(count)
	}
	fmt.Println("จบ")

//for range
	for index, value := range number {
		fmt.Println(index, value)
	}
//ไม่เอา index
	for _, value := range number {
		fmt.Println("value", value)
	}
}
---------------------------------------------------------------------------

Function
อาร์กิวเมนต์ คือ ตัวแปลหรือค่าที่ต้องการส่งมาให้กับฟังก์ชีัน
พารามิเตอร์ ตือ ตัวแปลที่สร้างไว้สำหรับรับค่าที่จะส่งเข้ามาให้กับฟังก์ชั่น
1. ฟังก์ชันที่ไม่มีการรับค่าและส่งค่า
	func ชื่อฟังก์ชัน(){
		//คำสั่ง
	}

	การเรียกใช้ 
	ชื่อฟังก์ชัน()

2. ฟังก์ชันที่ไม่มีการรับค่าเข้ามาทำงาน
	func ชื่อฟังก์ชัน(parameter1, parameter2,...){
		//คำสั่ง
	}

	การเรียกใช้
	ชื่อฟังก์ชัน(parameter1, parameter2,...)

3. ฟังก์ชั่นที่มีการส่งค่าออกมา
	func ชื่อฟังก์ชัน(){
		//คำสั่ง
		return ค่าที่จะส่งออกไป
	}	

4. ฟังก์ชั่นที่รับค่าและมีการส่งค่าออกมา
	func ชื่อฟังก์ชัน(parameter1, parameter2,...){
		//คำสั่ง
		return ค่าที่จะส่งออกไป
	}	

ex.
func main(){
	showmessage()
	showmessagebyname("สมหญิง")
	name := funcre()
	fmt.Println(name)

	sum, num := total(50, 2)
	fmt.Println("เลข ",num,"ยอดรวม ", sum)

		fmt.Println(summstion(10,20,30,40,50))
}

func showmessage(){
	fmt.Println("Hi")
}

func showmessagebyname(name string){
	fmt.Println("Hi", name)
}

func  funcre() string  {
	return "สมศรี"
}

func total(price , total int) (int, string) {
	sum := price * total
	status := ""
	if sum%2 == 0{
		status = "เลขคู่"
	}else{
		status = "เลขคี่"
	}
	return sum, status
}

//ส่ง data numbers มาได้ไม่จำกัดจำนวน
func summstion(numbers ...int) int{
	total := 0
	for _, value := range numbers{
		total += value
	}

	return total
}
---------------------------------------------------------------------------

Structure
คือ การเอาข้อมูลต่างกันมารวมกัน
รูปแบบการใช้งาน
type ชื่อ struct{
	ตัวแปล1 ชนิดข้อมูล
	ตัวแปล2 ชนิดข้อมูล
}

ex. ===>
type Product struct{
	name string
	price float64
	category string
	discount int
}

func main(){
	product := Product{
		name:"ปากกา",
		price: 50.00,
		category: "เครื่องเขียน",
		discount: 10,
	}
	product2 := Product{
		name:"ปากกา",
		price: 50.00,
		category: "เครื่องเขียน",
		discount: 10,
	}

	fmt.Println(product,product2)
}
---------------------------------------------------------------------------

Package
คือการจัดโค้เป็นกลุ่ม
import "{ชื่อ package}"

การตั้งค่าให้ข้างนอกเข้าถึงได้ให้ตั้งชื่อ func อักษรตัวแรกเป็นตัพิมพ์ใหญ่


ex ===>
package main

import (
	"fmt"
	"gobasic/calcuter"
)

func main(){
	fmt.Println(calcuter.Add(50,60))
	fmt.Println(calcuter.Subtract(500,200))
}


** app.go
func main(){
	fmt.Println(calcuter.Add(50,60))
}

package calcuter

func Add(number1, number2 int)  int {
	return number1 + number2
}

func Subtract(number1, number2 int) int{
	return number1 - number2
}