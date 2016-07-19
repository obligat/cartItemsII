# cartItemsII
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script>
        let Items=[
            {

                barcode:"0001",
                name:"apple",
                unit:"ge",
                price:4.00
            },
            {
                barcode:"0002",
                name:'pear',
                unit:"ge",
                price:5.00
            },
            {
                barcode:"0001",
                name:'apple',
                unit:"ge",
                price:4.00
            }
        ];
        function computeCount(cartItems) {
            let countedItems=[];
            for(let i=0;i<cartItems.length;i++){
                let existItem=countedItems.find(function (item) {
                    return item.barcode===cartItems[i].barcode;
                });
                if(existItem){
                    existItem.count++;
                }else{
                    countedItems.push(Object.assign({},cartItems[i],{count:1}));
                }
            }
            return countedItems;
        }
        function calculateSubtotal(cartItems) {
            let subtotalResult=[];
            for(let i=0;i<cartItems.length;i++) {
                let subtotal = cartItems[i].price * cartItems[i].count;
                subtotalResult.push(Object.assign({},cartItems[i],{subtotal:subtotal}));
            }
            return subtotalResult;
        }
        function calculateTotal(cartItems) {
            let totalResult=0;
            for(let i=0;i<cartItems.length;i++) {
                totalResult+=cartItems[i].subtotal;
            }
            return totalResult;
        }
        function print(cartItems,total){
            for(let i=0;i<cartItems.length;i++){
                console.log("商品:"+cartItems[i].name+", 价格:"+cartItems[i].price+", 数量:"+cartItems[i].count);
            }
          /*  console.log(""+Items[0].name+","+Items[0].price+","+Items[0].count);
            console.log(""+Items[1].name+","+Items[1].price+","+Items[1].count);*/
            console.log("总计: "+total);
        }
        function printReceipts(cartItems){
            let count=computeCount(cartItems);
            let subtotal=calculateSubtotal(count);
            let total=calculateTotal(subtotal);
            print(count,total);
        }
        printReceipts(Items);
    </script>
    <title>my first code</title>
</head>
<body>

</body>
</html>
