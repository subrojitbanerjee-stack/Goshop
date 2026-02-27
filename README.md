<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>goshop</title>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
<style>
body{margin:0;font-family:Poppins, sans-serif;background:#f5f5f5}
header{position:fixed;top:0;width:100%;background:#fff;padding:10px 20px;box-shadow:0 2px 5px rgba(0,0,0,.1);z-index:100}
.hero{height:100vh;background:url('https://i.ibb.co/HfyQ1LYr/20260227-232513.jpg') center/cover no-repeat;display:flex;flex-direction:column;justify-content:center;align-items:center;color:#fff;text-align:center}
.hero h1{font-size:3em;margin:0}
.hero button{padding:10px 20px;font-size:18px;background:#000;color:#fff;border:none;cursor:pointer}
.products{padding:60px 20px}
.carousel{display:flex;overflow-x:auto;gap:20px}
.card{min-width:250px;background:#fff;padding:10px;border-radius:10px;text-align:center}
.card img{width:100%;border-radius:10px}
button{padding:8px 15px;background:black;color:white;border:none;cursor:pointer}
.cart{position:fixed;top:20px;right:20px;background:black;color:white;padding:10px;border-radius:50%;cursor:pointer}
.cart-modal{position:fixed;bottom:0;width:100%;background:#fff;padding:20px;display:none}
.whatsapp{position:fixed;bottom:20px;right:20px;background:green;color:white;padding:15px;border-radius:50%}
</style>
</head>
<body><header>
<h2>goshop - Fresh Finds, Best Prices</h2>
</header><section class="hero">
<h1>Welcome to goshop</h1>
<button onclick="document.getElementById('products').scrollIntoView()">Shop Now</button>
</section><section class="products" id="products">
<h2>Products</h2>
<div class="carousel" id="productList"></div>
</section><div class="cart" onclick="toggleCart()">🛒 <span id="count">0</span></div><div class="cart-modal" id="cartModal">
<h3>Your Cart</h3>
<div id="cartItems"></div>
<input placeholder="Name" id="name"><br><br>
<input placeholder="Phone" id="phone"><br><br>
<button onclick="sendOrder()">Send Order</button>
</div><a href="https://wa.me/99999999" class="whatsapp">💬</a>

<script>
const products=[
{img:'https://i.ibb.co/yFr0P33p/image.jpg',name:'Product 1',price:100},
{img:'https://i.ibb.co/chKzpf73/image.jpg',name:'Product 2',price:150},
{img:'https://i.ibb.co/PG9tSjFw/image.jpg',name:'Product 3',price:200},
{img:'https://i.ibb.co/8ngXmC92/515-R4-CLGOHL-AC-UF894-1000-QL80-FMwebp.webp',name:'Product 4',price:250},
{img:'https://i.ibb.co/gMF8wMMH/d9a73e0a7d79e654af7353c1e33744b2.jpg',name:'Product 5',price:300},
{img:'https://i.ibb.co/MxXNQjxX/35cae80761902d61b4d240ccda344bd3.jpg',name:'Product 6',price:350},
{img:'https://i.ibb.co/chBWCL68/a9a01cfc497ab4b4d53514e92eeeaf63.jpg',name:'Product 7',price:400},
{img:'https://i.ibb.co/bj4cz2T6/eb53bd23a5d545353735c29e12e2923c.jpg',name:'Product 8',price:450}
];

let cart=[];

const productList=document.getElementById('productList');
products.forEach((p,i)=>{
productList.innerHTML+=`<div class="card"><img src="${p.img}"><h3>${p.name}</h3><p>₹${p.price}</p><button onclick="addToCart(${i})">Add to Cart</button></div>`;
});

function addToCart(i){cart.push(products[i]);updateCart()}
function updateCart(){document.getElementById('count').innerText=cart.length;
document.getElementById('cartItems').innerHTML=cart.map(p=>p.name+" - ₹"+p.price).join('<br>')}

function toggleCart(){let m=document.getElementById('cartModal');m.style.display=m.style.display=='block'?'none':'block'}

function sendOrder(){
let name=document.getElementById('name').value;
let phone=document.getElementById('phone').value;
let items=cart.map(p=>p.name).join(', ');
let mailto=`mailto:subrojitbanerjee@gmail.com?subject=New Order&body=Name:${name}%0APhone:${phone}%0AItems:${items}`;
window.location.href=mailto;
}
</script></body>
</html>
