<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>UltraPOS Pro XXL</title>
  <style>
    :root{
      --bg:#070b17;--bg2:#0d1428;--panel:#121a33;--panel2:#1a2445;--panel3:#22305a;
      --text:#eef3ff;--muted:#98a7d9;--border:rgba(255,255,255,.12);
      --primary:#7b72ff;--primary2:#a397ff;--success:#21c07a;--warning:#ffbf47;--danger:#ff5f6d;
      --radius:16px;--shadow:0 14px 34px rgba(0,0,0,.35);
    }
    body.light{
      --bg:#f3f6ff;--bg2:#e8eefc;--panel:#ffffff;--panel2:#f7f9ff;--panel3:#eef3ff;
      --text:#1f2a44;--muted:#66759f;--border:rgba(31,42,68,.13);
      --shadow:0 10px 30px rgba(31,42,68,.12);
    }
    *{box-sizing:border-box} html,body{height:100%}
    body{
      margin:0;font-family:Inter,Segoe UI,Arial,sans-serif;color:var(--text);
      background:
      radial-gradient(1000px 600px at -10% -20%, rgba(123,114,255,.25), transparent 45%),
      radial-gradient(900px 520px at 115% -20%, rgba(33,192,122,.12), transparent 40%),
      linear-gradient(160deg,var(--bg),var(--bg2));
    }
    header{
      position:sticky;top:0;z-index:99;display:flex;justify-content:space-between;align-items:center;
      padding:12px 16px;background:color-mix(in oklab, var(--bg) 82%, transparent);
      backdrop-filter:blur(8px);border-bottom:1px solid var(--border)
    }
    .brand{font-weight:900;letter-spacing:.8px;background:linear-gradient(120deg,#fff,#d4dcff,#a397ff);-webkit-background-clip:text;color:transparent}
    .top{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
    .pill{padding:8px 10px;border:1px solid var(--border);border-radius:999px;background:rgba(255,255,255,.05);color:var(--muted)}
    .wrap{max-width:1500px;margin:18px auto;padding:0 14px}
    .card{background:linear-gradient(180deg,rgba(255,255,255,.04),rgba(255,255,255,.02)),var(--panel);border:1px solid var(--border);border-radius:16px;box-shadow:var(--shadow);padding:14px}
    .login{max-width:440px;margin:42px auto}
    nav{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:12px;padding:10px;border:1px solid var(--border);border-radius:14px;background:rgba(255,255,255,.03);position:sticky;top:64px;z-index:90}
    .grid-5{display:grid;grid-template-columns:repeat(5,1fr);gap:12px}
    .grid-4{display:grid;grid-template-columns:repeat(4,1fr);gap:12px}
    .grid-3{display:grid;grid-template-columns:repeat(3,1fr);gap:12px}
    .grid-2{display:grid;grid-template-columns:repeat(2,1fr);gap:12px}
    .row{display:flex;justify-content:space-between;align-items:center;gap:8px;flex-wrap:wrap}
    .item{border:1px solid var(--border);border-radius:12px;background:rgba(255,255,255,.04);padding:10px;margin:8px 0}
    .muted{color:var(--muted);font-size:.92rem}
    .badge{font-size:.78rem;padding:4px 8px;border-radius:999px;border:1px solid var(--border);background:rgba(255,255,255,.08)}
    .dot{display:inline-block;min-width:18px;padding:2px 6px;border-radius:999px;background:var(--danger);color:#fff;font-size:.72rem;text-align:center}
    button,input,select,textarea{font:inherit}
    button{
      border:none;border-radius:11px;padding:9px 11px;font-weight:700;cursor:pointer;color:#fff;
      background:linear-gradient(135deg,var(--primary),var(--primary2));
    }
    button.alt{background:linear-gradient(180deg,var(--panel3),var(--panel2));border:1px solid var(--border);color:var(--text)}
    button.success{background:linear-gradient(135deg,#179a5f,var(--success))}
    button.warn{background:linear-gradient(135deg,#d89a20,var(--warning));color:#171717}
    button.danger{background:linear-gradient(135deg,#e84a62,var(--danger))}
    button.small{padding:6px 8px;font-size:.82rem}
    input,select,textarea{
      width:100%;padding:10px;border-radius:11px;border:1px solid var(--border);
      color:var(--text);background:rgba(255,255,255,.05);margin:5px 0 9px
    }
    textarea{min-height:90px;resize:vertical}
    .hidden{display:none}
    .ok,.error{display:none;padding:9px 10px;border-radius:10px;margin-top:8px;font-weight:600}
    .ok{border:1px solid rgba(33,192,122,.45);background:rgba(33,192,122,.12);color:#bff7df}
    .error{border:1px solid rgba(255,95,109,.45);background:rgba(255,95,109,.12);color:#ffd5d9}
    .kpi{font-size:1.35rem;font-weight:900}
    .progress{height:8px;border-radius:999px;background:rgba(255,255,255,.12);overflow:hidden}
    .bar{height:100%;background:linear-gradient(90deg,var(--primary),var(--success))}
    @media(max-width:1220px){.grid-5,.grid-4,.grid-3,.grid-2{grid-template-columns:1fr}}
  </style>
</head>
<body>
<header>
  <div class="brand">ULTRAPOS PRO XXL</div>
  <div class="top">
    <div id="userBox" class="pill">Non connecté</div>
    <button id="themeBtn" class="alt" type="button">🌗 Thème</button>
    <button id="lockBtn" class="warn hidden" type="button">Verrouiller</button>
    <button id="logoutBtn" class="danger hidden" type="button">Déconnexion</button>
  </div>
</header>

<div class="wrap">
  <section id="loginSection" class="card login">
    <h2>Connexion</h2>
    <input id="pin" placeholder="PIN (1234 admin)" />
    <button id="loginBtn" type="button">Se connecter</button>
    <div id="okBox" class="ok"></div>
    <div id="errorBox" class="error"></div>
  </section>

  <section id="appSection" class="hidden">
    <nav>
      <button class="alt" onclick="showView('dashboard')">🏠 Dashboard</button>
      <button class="alt" onclick="showView('cash')">🧾 Caisse</button>
      <button class="alt" onclick="showView('kitchen')">🍳 Cuisine</button>
      <button class="alt" onclick="showView('reception')">🎟️ Réservations</button>
      <button class="alt" onclick="showView('customers')">👥 Clients</button>
      <button class="alt" onclick="showView('crm')">💬 Client↔Entreprise <span id="crmNotif" class="dot">0</span></button>
      <button class="alt" onclick="showView('staffChat')">🗨️ Chat Équipe <span id="staffNotif" class="dot">0</span></button>
      <button id="statsBtn" class="alt" onclick="showView('stats')">📊 Stats</button>
      <button id="adminBtn" class="alt" onclick="showView('admin')">⚙️ Admin</button>
      <button id="auditBtn" class="alt" onclick="showView('audit')">🕵️ Audit</button>
      <button class="alt" onclick="showView('tools')">🧰 Outils</button>
    </nav>

    <div id="dashboard" class="view">
      <div class="grid-5">
        <div class="card"><div class="muted">CA Jour</div><div class="kpi"><span id="kpiCa">0</span>€</div></div>
        <div class="card"><div class="muted">Ventes Jour</div><div class="kpi" id="kpiSales">0</div></div>
        <div class="card"><div class="muted">Réservations</div><div class="kpi" id="kpiBookings">0</div></div>
        <div class="card"><div class="muted">Stock Bas</div><div class="kpi" id="kpiLowStock">0</div></div>
        <div class="card"><div class="muted">Clients</div><div class="kpi" id="kpiCustomers">0</div></div>
      </div>
      <div class="grid-2" style="margin-top:12px">
        <div class="card"><h3>Alertes</h3><div id="alerts"></div></div>
        <div class="card"><h3>Activité récente</h3><div id="recentAudit"></div></div>
      </div>
    </div>

    <div id="cash" class="view hidden">
      <div class="grid-4">
        <div class="card">
          <h3>Produits</h3>
          <input id="productSearch" placeholder="Rechercher..." oninput="renderCashProducts()"/>
          <div id="products"></div>
        </div>
        <div class="card">
          <h3>Panier</h3>
          <div id="cart"></div>
          <div class="item">
            <label>Remise %</label><input id="discount" type="number" min="0" max="100" value="0" oninput="render()">
            <label>Taxe %</label><input id="tax" type="number" min="0" max="100" value="10" oninput="render()">
            <label>Coupon</label><input id="coupon" placeholder="Ex: WELCOME10">
            <button class="small alt" onclick="applyCoupon()">Appliquer coupon</button>
            <p>Sous-total: <strong><span id="subTotal">0.00</span>€</strong></p>
            <p>Remise: <strong>-<span id="discountValue">0.00</span>€</strong></p>
            <p>Taxe: <strong>+<span id="taxValue">0.00</span>€</strong></p>
            <p>Total: <strong><span id="total">0.00</span>€</strong></p>
          </div>
          <div class="row">
            <button class="success" onclick="pay()">Encaisser</button>
            <button class="alt" onclick="clearCart()">Vider</button>
          </div>
        </div>
        <div class="card">
          <h3>Paiement</h3>
          <div class="row">
            <button class="alt" onclick="setPay('CB')">CB</button>
            <button class="alt" onclick="setPay('Cash')">Cash</button>
            <button class="alt" onclick="setPay('QR')">QR</button>
            <button class="alt" onclick="setPay('Mobile')">Mobile</button>
          </div>
          <p class="muted">Mode: <span id="payMode">CB</span></p>
          <label>Client</label>
          <input id="customerName" placeholder="Nom client">
          <button class="small alt" onclick="attachCustomer()">Lier client / créer</button>
        </div>
        <div class="card">
          <h3>Ticket + ventes récentes</h3>
          <div id="receipt"></div><hr style="border-color:var(--border)">
          <div id="quickSales"></div>
        </div>
      </div>
    </div>

    <div id="kitchen" class="view hidden"><div class="card"><div class="row"><h3>Écran Cuisine</h3><div class="row"><button class="alt" onclick="setKitchenFilter('all')">Tout</button><button class="warn" onclick="setKitchenFilter('ready')">À préparer</button><button class="alt" onclick="setKitchenFilter('cooking')">En cours</button><button class="success" onclick="setKitchenFilter('done')">Terminé</button></div></div><div id="orders"></div></div></div>

    <div id="reception" class="view hidden"><div class="grid-2"><div class="card"><h3>Nouvelle réservation</h3><input id="client" placeholder="Client"><select id="activity"></select><input id="time" placeholder="Heure ex 14:00"><input id="peopleCount" type="number" min="1" value="1"><input id="zone" placeholder="Zone/Table ex A3"><button onclick="addBooking()">Réserver</button></div><div class="card"><h3>Liste</h3><input id="bookingSearch" placeholder="Recherche..." oninput="render()"><div id="bookings"></div></div></div></div>

    <div id="customers" class="view hidden"><div class="grid-2"><div class="card"><h3>Nouveau client</h3><input id="cName" placeholder="Nom"><input id="cEmail" placeholder="Email"><input id="cPhone" placeholder="Téléphone"><button onclick="addCustomer()">Ajouter client</button></div><div class="card"><h3>Base clients</h3><input id="customerSearch" placeholder="Recherche client..." oninput="render()"><div id="customersList"></div></div></div></div>

    <div id="crm" class="view hidden">
      <div class="grid-2">
        <div class="card">
          <h3>Nouveau message client</h3>
          <input id="crmClientName" placeholder="Nom client">
          <input id="crmClientContact" placeholder="Email / téléphone">
          <select id="crmTopic">
            <option>Question</option><option>Réclamation</option><option>Demande de réservation</option><option>Partenariat</option>
          </select>
          <textarea id="crmMessage" placeholder="Message client..."></textarea>
          <button onclick="createClientTicket()">Créer ticket</button>
        </div>
        <div class="card">
          <h3>Tickets clients</h3>
          <select id="crmFilter" onchange="render()">
            <option value="all">Tous</option><option value="open">Ouvert</option><option value="pending">En cours</option><option value="closed">Clos</option>
          </select>
          <div id="crmList"></div>
        </div>
      </div>
    </div>

    <div id="staffChat" class="view hidden">
      <div class="grid-2">
        <div class="card">
          <h3>Envoyer un message interne</h3>
          <select id="chatTo">
            <option value="all">Canal Général (toute l'équipe)</option>
          </select>
          <textarea id="chatText" placeholder="Message interne..."></textarea>
          <button onclick="sendStaffMessage()">Envoyer</button>
        </div>
        <div class="card">
          <h3>Flux équipe</h3>
          <select id="chatFilter" onchange="render()">
            <option value="mine">Messages me concernant</option>
            <option value="all">Tous les messages</option>
          </select>
          <div id="staffChatList"></div>
        </div>
      </div>
    </div>

    <div id="stats" class="view hidden"><div class="grid-4"><div class="card"><h3>CA total</h3><div class="kpi"><span id="ca">0</span>€</div></div><div class="card"><h3>Ventes</h3><div class="kpi" id="salesCount">0</div></div><div class="card"><h3>Réservations</h3><div class="kpi" id="bookCount">0</div></div><div class="card"><h3>Panier moyen</h3><div class="kpi"><span id="avgTicket">0</span>€</div></div></div><div class="grid-2" style="margin-top:12px"><div class="card"><h3>CA par mode</h3><div id="caByMode"></div></div><div class="card"><h3>Top produits</h3><div id="topProducts"></div></div></div></div>

    <div id="admin" class="view hidden"><div class="grid-3"><div class="card"><h3>Produits & stock</h3><input id="pname" placeholder="Produit"><input id="pprice" type="number" min="0" placeholder="Prix"><input id="pstock" type="number" min="0" placeholder="Stock initial"><button onclick="addProduct()">Ajouter</button><div id="productAdminList"></div></div><div class="card"><h3>Activités / coupons</h3><input id="aname" placeholder="Activité"><button onclick="addActivity()">Ajouter activité</button><hr style="border-color:var(--border)"><input id="couponCode" placeholder="Code coupon"><input id="couponPct" type="number" min="1" max="80" placeholder="% remise"><button onclick="addCoupon()">Ajouter coupon</button><div id="activityAdminList"></div><div id="couponList"></div></div><div class="card"><h3>Employés</h3><input id="ename" placeholder="Nom"><input id="ecode" placeholder="PIN"><select id="erole"><option>ADMIN</option><option>MANAGER</option><option>VENDEUR</option><option>CUISINE</option><option>ACCUEIL</option></select><button onclick="addEmployee()">Ajouter employé</button><div id="employees"></div></div></div></div>

    <div id="audit" class="view hidden"><div class="card"><div class="row"><h3>Journal d'audit</h3><button class="danger small" onclick="clearAudit()">Vider journal</button></div><div id="auditList"></div></div></div>

    <div id="tools" class="view hidden"><div class="grid-2"><div class="card"><h3>Export / Import</h3><button onclick="exportData()">Exporter JSON</button><input id="importText" placeholder="Coller JSON ici"><button class="warn" onclick="importData()">Importer JSON</button></div><div class="card"><h3>Rapport fin de journée</h3><button class="success" onclick="dailyReport()">Générer</button><div id="dailyReport"></div></div></div></div>
  </section>
</div>

<script>
let userRole=null,currentUser=null,kitchenFilter="all",cart=[],payMode="CB",lastReceipt=null,appliedCoupon=null,attachedCustomerId=null;
const defaultData={
  products:[{id:1,name:"Boisson",price:2,stock:40},{id:2,name:"Snack",price:3,stock:30}],
  activities:["Parc","Kid Park"],bookings:[],sales:[],orders:[],
  customers:[],coupons:[{code:"WELCOME10",pct:10,active:true}],
  crmTickets:[],staffMessages:[],commRead:{crm:{},staff:{}},
  employees:[
    {id:1,name:"Admin",code:"1234",role:"ADMIN",active:true},
    {id:2,name:"Manager",code:"1111",role:"MANAGER",active:true},
    {id:3,name:"Vendeur",code:"2222",role:"VENDEUR",active:true}
  ],
  audit:[],settings:{theme:"dark"},seq:{product:3,employee:4,customer:1}
};
const refs={},allowed={admin:["dashboard","cash","kitchen","reception","customers","crm","staffChat","stats","admin","audit","tools"],manager:["dashboard","cash","kitchen","reception","customers","crm","staffChat","stats","audit","tools"],vendeur:["dashboard","cash","customers","crm","staffChat","tools"],cuisine:["dashboard","kitchen","staffChat"],accueil:["dashboard","reception","customers","crm","staffChat"]};
function clone(o){return JSON.parse(JSON.stringify(o))}
function loadData(){try{const raw=JSON.parse(localStorage.getItem("ultraXXL"));if(!raw||typeof raw!=="object")return clone(defaultData);const d={...clone(defaultData),...raw};if(!d.seq)d.seq={product:100,employee:100,customer:100};if(!d.crmTickets)d.crmTickets=[];if(!d.staffMessages)d.staffMessages=[];if(!d.commRead)d.commRead={crm:{},staff:{}};return d}catch{return clone(defaultData)}}
let data=loadData();
function save(){localStorage.setItem("ultraXXL",JSON.stringify(data))}
function log(action,detail=""){data.audit.unshift({id:Date.now()+Math.random(),date:new Date().toLocaleString(),user:currentUser?currentUser.name:"system",action,detail});if(data.audit.length>500)data.audit.pop();save()}
function initRefs(){["loginSection","appSection","pin","loginBtn","logoutBtn","lockBtn","themeBtn","userBox","okBox","errorBox","statsBtn","adminBtn","auditBtn","products","cart","discount","tax","coupon","subTotal","discountValue","taxValue","total","payMode","customerName","receipt","quickSales","orders","activity","client","time","peopleCount","zone","bookings","bookingSearch","kpiCa","kpiSales","kpiBookings","kpiLowStock","kpiCustomers","alerts","recentAudit","customersList","customerSearch","cName","cEmail","cPhone","ca","salesCount","bookCount","avgTicket","caByMode","topProducts","pname","pprice","pstock","aname","productAdminList","activityAdminList","couponCode","couponPct","couponList","ename","ecode","erole","employees","auditList","importText","dailyReport","productSearch","crmClientName","crmClientContact","crmTopic","crmMessage","crmFilter","crmList","chatTo","chatText","chatFilter","staffChatList","crmNotif","staffNotif"].forEach(id=>refs[id]=document.getElementById(id))}
function showError(m){refs.errorBox.style.display="block";refs.errorBox.textContent=m;refs.okBox.style.display="none"}
function showOk(m){refs.okBox.style.display="block";refs.okBox.textContent=m;refs.errorBox.style.display="none"}
function clearMsg(){refs.okBox.style.display=refs.errorBox.style.display="none";refs.okBox.textContent=refs.errorBox.textContent=""}
function applyTheme(){document.body.classList.toggle("light",data.settings.theme==="light")}
function toggleTheme(){data.settings.theme=data.settings.theme==="light"?"dark":"light";save();applyTheme()}
function me(){return currentUser?currentUser.name:"system"}
function markRead(type){if(!currentUser)return;const key=currentUser.id;const maxId=(type==="crm"?data.crmTickets:data.staffMessages).reduce((m,x)=>Math.max(m,x.id||0),0);data.commRead[type][key]=maxId;save()}

function login(){clearMsg();const pin=refs.pin.value.trim();if(!pin)return showError("PIN requis");const emp=data.employees.find(e=>String(e.code)===pin&&e.active!==false);if(!emp)return showError("PIN invalide");userRole=emp.role.toLowerCase();currentUser=emp;refs.userBox.textContent=`${emp.name} • ${emp.role}`;refs.loginSection.classList.add("hidden");refs.appSection.classList.remove("hidden");refs.logoutBtn.classList.remove("hidden");refs.lockBtn.classList.remove("hidden");refs.pin.value="";log("LOGIN",emp.role);render();showView("dashboard");showOk("Connexion OK")}
function secureLogout(msg){userRole=null;currentUser=null;cart=[];appliedCoupon=null;attachedCustomerId=null;refs.customerName.value="";refs.userBox.textContent="Non connecté";refs.appSection.classList.add("hidden");refs.loginSection.classList.remove("hidden");refs.logoutBtn.classList.add("hidden");refs.lockBtn.classList.add("hidden");clearMsg();if(msg)showOk(msg)}
function logout(){log("LOGOUT","");secureLogout("Déconnecté")}
function lockSession(){log("LOCK","");secureLogout("Session verrouillée")}
function can(view){return !!(allowed[userRole]||[]).includes(view)}
function showView(id){if(!can(id))return alert("Accès refusé");document.querySelectorAll(".view").forEach(v=>v.classList.add("hidden"));document.getElementById(id).classList.remove("hidden");if(id==="crm")markRead("crm");if(id==="staffChat")markRead("staff");render()}
function setPay(m){payMode=m;render()}
function addCart(id){const p=data.products.find(x=>x.id===id);if(!p)return;if(p.stock<=0)return showError("Rupture de stock");const f=cart.find(c=>c.id===id);if(f){if(f.qty>=p.stock)return showError("Stock max atteint");f.qty++}else cart.push({id:p.id,n:p.name,p:p.price,qty:1});render()}
function incItem(id){const i=cart.find(x=>x.id===id),p=data.products.find(x=>x.id===id);if(i&&p&&i.qty<p.stock){i.qty++;render()}}
function decItem(id){const i=cart.find(x=>x.id===id);if(!i)return;i.qty--;if(i.qty<=0)cart=cart.filter(x=>x.id!==id);render()}
function removeItem(id){cart=cart.filter(x=>x.id!==id);render()}
function clearCart(){cart=[];appliedCoupon=null;attachedCustomerId=null;render()}
function applyCoupon(){const c=refs.coupon.value.trim().toUpperCase();if(!c)return;const found=data.coupons.find(x=>x.code===c&&x.active);if(!found)return showError("Coupon invalide");appliedCoupon=found;showOk("Coupon appliqué");render()}
function attachCustomer(){const n=refs.customerName.value.trim();if(!n)return;let c=data.customers.find(x=>x.name.toLowerCase()===n.toLowerCase());if(!c){c={id:data.seq.customer++,name:n,email:"",phone:"",points:0,spent:0};data.customers.push(c);log("CUSTOMER_AUTO_CREATE",n)}attachedCustomerId=c.id;save();showOk(`Client lié: ${c.name}`);render()}
function totals(){const sub=cart.reduce((a,b)=>a+b.p*b.qty,0),disc=Math.max(0,Math.min(100,+refs.discount.value||0)),tax=Math.max(0,Math.min(100,+refs.tax.value||0));let discountValue=sub*(disc/100);if(appliedCoupon)discountValue+=sub*(appliedCoupon.pct/100);if(discountValue>sub)discountValue=sub;const taxed=(sub-discountValue)*(tax/100);return{sub,discountValue,taxed,total:sub-discountValue+taxed}}
function pay(){if(!cart.length)return showError("Panier vide");for(const l of cart){const p=data.products.find(x=>x.id===l.id);if(!p||p.stock<l.qty)return showError(`Stock insuffisant: ${l.n}`)}const t=totals();const sale={id:Date.now(),lines:cart.map(i=>({...i})),subTotal:t.sub,discountValue:t.discountValue,taxValue:t.taxed,total:t.total,mode:payMode,date:new Date().toLocaleString(),cashier:currentUser?currentUser.name:"N/A",coupon:appliedCoupon?appliedCoupon.code:null,customerId:attachedCustomerId||null,customer:refs.customerName.value.trim()||"Walk-in"};data.sales.push(sale);cart.forEach(l=>{const p=data.products.find(x=>x.id===l.id);p.stock-=l.qty});if(sale.customerId){const c=data.customers.find(x=>x.id===sale.customerId);if(c){const pts=Math.floor(sale.total/5);c.points+=pts;c.spent=(c.spent||0)+sale.total}}data.orders.push({id:Date.now()+1,items:sale.lines,status:"ready",priority:t.total>30?"high":"normal",createdAt:new Date().toLocaleString(),startedAt:null,doneAt:null,prep:0});lastReceipt=sale;cart=[];appliedCoupon=null;attachedCustomerId=null;refs.customerName.value="";refs.coupon.value="";log("SALE",`${sale.total.toFixed(2)}€ ${sale.mode}`);save();render();showOk("Paiement OK")}
function setKitchenFilter(f){kitchenFilter=f;render()}
function setOrderStatus(id,status){const o=data.orders.find(x=>x.id===id);if(!o)return;o.status=status;if(status==="cooking"&&!o.startedAt)o.startedAt=new Date().toLocaleString();if(status==="done"){o.doneAt=new Date().toLocaleString();o.prep=100}log("KITCHEN_STATUS",`#${id} ${status}`);save();render()}
function setPrep(id,val){const o=data.orders.find(x=>x.id===id);if(!o)return;o.prep=Math.max(0,Math.min(100,+val||0));if(o.prep>0&&o.status==="ready")o.status="cooking";if(o.prep===100)o.status="done";save();render()}
function addBooking(){const name=refs.client.value.trim(),time=refs.time.value.trim(),activity=refs.activity.value,people=Math.max(1,+refs.peopleCount.value||1),zone=refs.zone.value.trim()||"N/A";if(!name||!time)return showError("Nom/heure requis");data.bookings.push({id:Date.now(),name,activity,time,people,zone,status:"check-in"});refs.client.value=refs.time.value=refs.zone.value="";refs.peopleCount.value="1";log("BOOKING_ADD",name);save();render()}
function setBookingStatus(id,status){const b=data.bookings.find(x=>x.id===id);if(!b)return;b.status=status;log("BOOKING_STATUS",`#${id} ${status}`);save();render()}
function addCustomer(){const name=refs.cName.value.trim();if(!name)return showError("Nom requis");data.customers.push({id:data.seq.customer++,name,email:refs.cEmail.value.trim(),phone:refs.cPhone.value.trim(),points:0,spent:0});refs.cName.value=refs.cEmail.value=refs.cPhone.value="";log("CUSTOMER_ADD",name);save();render();showOk("Client ajouté")}
function addProduct(){if(userRole!=="admin")return alert("Admin only");const n=refs.pname.value.trim(),p=+refs.pprice.value,s=Math.max(0,+refs.pstock.value||0);if(!n||isNaN(p)||p<0)return showError("Produit invalide");data.products.push({id:data.seq.product++,name:n,price:p,stock:s});refs.pname.value=refs.pprice.value=refs.pstock.value="";log("PRODUCT_ADD",n);save();render()}
function updateStock(id,delta){const p=data.products.find(x=>x.id===id);if(!p)return;p.stock=Math.max(0,p.stock+delta);log("STOCK_UPDATE",`${p.name} ${delta>0?"+":""}${delta}`);save();render()}
function delProduct(id){if(userRole!=="admin")return;const p=data.products.find(x=>x.id===id);data.products=data.products.filter(x=>x.id!==id);log("PRODUCT_DEL",p?p.name:id);save();render()}
function addActivity(){const n=refs.aname.value.trim();if(!n)return;if(data.activities.includes(n))return showError("Déjà existante");data.activities.push(n);refs.aname.value="";log("ACTIVITY_ADD",n);save();render()}
function delActivity(n){data.activities=data.activities.filter(a=>a!==n);log("ACTIVITY_DEL",n);save();render()}
function addCoupon(){if(userRole!=="admin")return;const code=refs.couponCode.value.trim().toUpperCase(),pct=Math.max(1,Math.min(80,+refs.couponPct.value||0));if(!code||!pct)return showError("Coupon invalide");if(data.coupons.some(c=>c.code===code))return showError("Code existe");data.coupons.push({code,pct,active:true});refs.couponCode.value=refs.couponPct.value="";log("COUPON_ADD",`${code} ${pct}%`);save();render()}
function toggleCoupon(code){const c=data.coupons.find(x=>x.code===code);if(!c)return;c.active=!c.active;log("COUPON_TOGGLE",`${code} ${c.active}`);save();render()}
function addEmployee(){if(userRole!=="admin")return;const n=refs.ename.value.trim(),c=refs.ecode.value.trim(),r=refs.erole.value;if(!n||!c)return showError("Employé invalide");if(data.employees.some(e=>String(e.code)===c))return showError("PIN déjà utilisé");data.employees.push({id:data.seq.employee++,name:n,code:c,role:r,active:true});refs.ename.value=refs.ecode.value="";refs.erole.value="ADMIN";log("EMP_ADD",`${n} ${r}`);save();render()}
function toggleEmployee(id){const e=data.employees.find(x=>x.id===id);if(!e)return;e.active=!e.active;log("EMP_TOGGLE",`${e.name} ${e.active}`);save();render()}
function clearAudit(){if(userRole!=="admin")return;data.audit=[];save();render()}
function exportData(){refs.importText.value=JSON.stringify(data);showOk("Export JSON prêt (copier le champ)")}
function importData(){if(userRole!=="admin")return;try{const parsed=JSON.parse(refs.importText.value||"{}");if(!parsed||typeof parsed!=="object")throw new Error();data={...clone(defaultData),...parsed};save();log("IMPORT","JSON");render();showOk("Import OK")}catch{showError("JSON invalide")}}
function dailyReport(){const today=new Date().toLocaleDateString();const sales=data.sales.filter(s=>s.date.includes(today));const ca=sales.reduce((a,b)=>a+b.total,0);const byMode={};sales.forEach(s=>byMode[s.mode]=(byMode[s.mode]||0)+s.total);refs.dailyReport.innerHTML=`<div class="item"><strong>Rapport ${today}</strong><p>Ventes: ${sales.length}</p><p>CA: ${ca.toFixed(2)}€</p>${Object.entries(byMode).map(([k,v])=>`<p>${k}: ${v.toFixed(2)}€</p>`).join("")||"<p>Aucune vente</p>"}</div>`}

function createClientTicket(){
  const name=refs.crmClientName.value.trim(),contact=refs.crmClientContact.value.trim(),topic=refs.crmTopic.value,message=refs.crmMessage.value.trim();
  if(!name||!message)return showError("Nom client + message requis");
  data.crmTickets.unshift({id:Date.now(),date:new Date().toLocaleString(),clientName:name,contact,topic,message,status:"open",reply:"",owner:me()});
  refs.crmClientName.value=refs.crmClientContact.value=refs.crmMessage.value="";
  log("CRM_TICKET_CREATE",`${name} • ${topic}`);save();render();showOk("Ticket client créé")
}
function setTicketStatus(id,status){const t=data.crmTickets.find(x=>x.id===id);if(!t)return;t.status=status;log("CRM_TICKET_STATUS",`#${id} ${status}`);save();render()}
function replyTicket(id){const text=prompt("Réponse au client :","");if(text===null)return;const t=data.crmTickets.find(x=>x.id===id);if(!t)return;t.reply=text.trim();if(t.reply)t.status="pending";log("CRM_TICKET_REPLY",`#${id}`);save();render()}
function sendStaffMessage(){
  if(!currentUser)return;
  const to=refs.chatTo.value,text=refs.chatText.value.trim();if(!text)return showError("Message vide");
  data.staffMessages.unshift({id:Date.now(),date:new Date().toLocaleString(),fromId:currentUser.id,from:currentUser.name,to,txt:text});
  refs.chatText.value="";log("STAFF_MSG_SEND",`to:${to}`);save();render();showOk("Message envoyé")
}
function unreadCRM(){if(!currentUser)return 0;const last=data.commRead.crm[currentUser.id]||0;return data.crmTickets.filter(t=>t.id>last).length}
function unreadStaff(){if(!currentUser)return 0;const last=data.commRead.staff[currentUser.id]||0;return data.staffMessages.filter(m=>m.id>last&&(m.to==="all"||String(m.to)===String(currentUser.id)||m.fromId===currentUser.id)).length}

function renderCashProducts(){const q=(refs.productSearch.value||"").toLowerCase();refs.products.innerHTML=data.products.filter(p=>p.name.toLowerCase().includes(q)).map(p=>`<div class="item"><div class="row"><strong>${p.name}</strong><span>${p.price.toFixed(2)}€</span></div><div class="row"><span class="muted">Stock: ${p.stock}</span><button class="small" onclick="addCart(${p.id})">Ajouter</button></div></div>`).join("")}
function render(){
  applyTheme();
  refs.statsBtn.style.display=["admin","manager"].includes(userRole)?"inline-block":"none";
  refs.adminBtn.style.display=userRole==="admin"?"inline-block":"none";
  refs.auditBtn.style.display=["admin","manager"].includes(userRole)?"inline-block":"none";
  renderCashProducts();

  if(refs.chatTo){
    const emps=data.employees.filter(e=>e.active!==false&&(!currentUser||e.id!==currentUser.id));
    refs.chatTo.innerHTML=`<option value="all">Canal Général (toute l'équipe)</option>`+emps.map(e=>`<option value="${e.id}">DM: ${e.name}</option>`).join("");
  }

  const crmN=unreadCRM(), staffN=unreadStaff();
  refs.crmNotif.textContent=crmN; refs.staffNotif.textContent=staffN;
  refs.crmNotif.style.display=crmN>0?"inline-block":"none";
  refs.staffNotif.style.display=staffN>0?"inline-block":"none";

  refs.cart.innerHTML=cart.map(i=>`<div class="item"><div class="row"><strong>${i.n}</strong><span>${(i.p*i.qty).toFixed(2)}€</span></div><div class="row"><span class="muted">${i.p.toFixed(2)}€ x ${i.qty}</span><div><button class="small alt" onclick="decItem(${i.id})">-</button> <button class="small alt" onclick="incItem(${i.id})">+</button> <button class="small danger" onclick="removeItem(${i.id})">Suppr</button></div></div></div>`).join("")||`<p class="muted">Panier vide</p>`;
  const t=totals();refs.subTotal.textContent=t.sub.toFixed(2);refs.discountValue.textContent=t.discountValue.toFixed(2);refs.taxValue.textContent=t.taxed.toFixed(2);refs.total.textContent=t.total.toFixed(2);refs.payMode.textContent=payMode;
  refs.activity.innerHTML=data.activities.map(a=>`<option>${a}</option>`).join("");

  const crmFilter=refs.crmFilter.value||"all";
  refs.crmList.innerHTML=data.crmTickets.filter(t=>crmFilter==="all"||t.status===crmFilter).map(t=>`<div class="item"><div class="row"><strong>${t.clientName}</strong><span class="badge">${t.topic}</span></div><div class="muted">${t.contact||"-"} • ${t.date} • statut: ${t.status}</div><p>${t.message}</p>${t.reply?`<p class="muted"><strong>Réponse:</strong> ${t.reply}</p>`:""}<div class="row"><button class="small alt" onclick="setTicketStatus(${t.id},'open')">Ouvrir</button><button class="small warn" onclick="setTicketStatus(${t.id},'pending')">En cours</button><button class="small success" onclick="setTicketStatus(${t.id},'closed')">Clore</button><button class="small" onclick="replyTicket(${t.id})">Répondre</button></div></div>`).join("")||`<p class="muted">Aucun ticket</p>`;

  const chatFilter=refs.chatFilter.value||"mine";
  const messages=data.staffMessages.filter(m=>{
    if(chatFilter==="all") return true;
    if(!currentUser) return false;
    return m.to==="all"||String(m.to)===String(currentUser.id)||m.fromId===currentUser.id;
  });
  refs.staffChatList.innerHTML=messages.map(m=>`<div class="item"><div class="row"><strong>${m.from}</strong><span class="badge">${m.to==="all"?"Général":"DM"}</span></div><div class="muted">${m.date}</div><p>${m.txt}</p></div>`).join("")||`<p class="muted">Aucun message</p>`;

  const bq=(refs.bookingSearch.value||"").toLowerCase();
  refs.bookings.innerHTML=data.bookings.filter(b=>b.name.toLowerCase().includes(bq)).map(b=>`<div class="item"><div class="row"><strong>${b.name}</strong><span class="badge">${b.time}</span></div><div class="muted">${b.activity} • ${b.people} pers • zone ${b.zone} • ${b.status}</div><div class="row"><button class="small alt" onclick="setBookingStatus(${b.id},'check-in')">Check-in</button><button class="small success" onclick="setBookingStatus(${b.id},'done')">Terminé</button><button class="small danger" onclick="setBookingStatus(${b.id},'cancel')">Annulé</button></div></div>`).join("");
  refs.orders.innerHTML=data.orders.filter(o=>kitchenFilter==="all"||o.status===kitchenFilter).map(o=>`<div class="item"><div class="row"><strong>Commande #${o.id}</strong><span class="badge">${o.status} • ${o.priority}</span></div><div class="muted">${o.items.map(i=>`${i.n} x${i.qty}`).join(", ")}</div><div class="row"><input type="range" min="0" max="100" value="${o.prep||0}" oninput="setPrep(${o.id},this.value)"><span>${o.prep||0}%</span></div><div class="progress"><div class="bar" style="width:${o.prep||0}%"></div></div><div class="row" style="margin-top:8px"><button class="small warn" onclick="setOrderStatus(${o.id},'ready')">Ready</button><button class="small alt" onclick="setOrderStatus(${o.id},'cooking')">Cooking</button><button class="small success" onclick="setOrderStatus(${o.id},'done')">Done</button></div></div>`).join("");

  const cq=(refs.customerSearch.value||"").toLowerCase();
  refs.customersList.innerHTML=data.customers.filter(c=>c.name.toLowerCase().includes(cq)).map(c=>`<div class="item"><div class="row"><strong>${c.name}</strong><span class="badge">${c.points||0} pts</span></div><div class="muted">${c.email||"-"} • ${c.phone||"-"} • dépensé ${(c.spent||0).toFixed(2)}€</div></div>`).join("")||`<p class="muted">Aucun client</p>`;
  const ca=data.sales.reduce((a,b)=>a+b.total,0);refs.ca.textContent=ca.toFixed(2);refs.salesCount.textContent=data.sales.length;refs.bookCount.textContent=data.bookings.length;refs.avgTicket.textContent=(data.sales.length?ca/data.sales.length:0).toFixed(2);
  const modeMap={};data.sales.forEach(s=>modeMap[s.mode]=(modeMap[s.mode]||0)+s.total);refs.caByMode.innerHTML=Object.keys(modeMap).length?Object.entries(modeMap).map(([k,v])=>`<div class="item row"><strong>${k}</strong><span>${v.toFixed(2)}€</span></div>`).join(""):`<p class="muted">Aucune donnée</p>`;
  const prodMap={};data.sales.forEach(s=>s.lines.forEach(l=>prodMap[l.n]=(prodMap[l.n]||0)+l.qty));const top=Object.entries(prodMap).sort((a,b)=>b[1]-a[1]).slice(0,10);refs.topProducts.innerHTML=top.length?top.map(([k,v])=>`<div class="item row"><strong>${k}</strong><span>${v} vendus</span></div>`).join(""):`<p class="muted">Aucune donnée</p>`;
  refs.receipt.innerHTML=lastReceipt?`<div class="item"><strong>Ticket #${lastReceipt.id}</strong><div class="muted">${lastReceipt.date} • ${lastReceipt.cashier}</div><div class="muted">${lastReceipt.lines.map(l=>`${l.n} x${l.qty}`).join(", ")}</div><p>Total: <strong>${lastReceipt.total.toFixed(2)}€</strong></p>${lastReceipt.coupon?`<p class="muted">Coupon: ${lastReceipt.coupon}</p>`:""}</div>`:`<p class="muted">Aucun ticket récent</p>`;
  refs.quickSales.innerHTML=data.sales.slice(-5).reverse().map(s=>`<div class="item"><div class="row"><strong>#${s.id}</strong><span>${s.total.toFixed(2)}€</span></div><div class="muted">${s.mode} • ${s.cashier}</div></div>`).join("")||`<p class="muted">Pas de ventes</p>`;
  refs.productAdminList.innerHTML=data.products.map(p=>`<div class="item"><div class="row"><strong>${p.name}</strong><span>${p.price.toFixed(2)}€</span></div><div class="row"><span class="muted">Stock ${p.stock}${p.stock<5?" ⚠️":""}</span><div><button class="small alt" onclick="updateStock(${p.id},1)">+1</button> <button class="small alt" onclick="updateStock(${p.id},-1)">-1</button> <button class="small danger" onclick="delProduct(${p.id})">Suppr</button></div></div></div>`).join("");
  refs.activityAdminList.innerHTML=data.activities.map(a=>`<div class="item row"><span>${a}</span><button class="small danger" onclick="delActivity('${a.replace(/'/g,"\\'")}')">Suppr</button></div>`).join("");
  refs.couponList.innerHTML=data.coupons.map(c=>`<div class="item row"><span><strong>${c.code}</strong> - ${c.pct}%</span><button class="small ${c.active?"warn":"success"}" onclick="toggleCoupon('${c.code}')">${c.active?"Désactiver":"Activer"}</button></div>`).join("");
  refs.employees.innerHTML=data.employees.map(e=>`<div class="item"><div class="row"><strong>${e.name}</strong><span class="badge">${e.role}</span></div><div class="muted">PIN: ${e.code} • ${e.active?"Actif":"Inactif"}</div><button class="small ${e.active?"warn":"success"}" onclick="toggleEmployee(${e.id})">${e.active?"Désactiver":"Activer"}</button></div>`).join("");
  refs.auditList.innerHTML=data.audit.slice(0,200).map(a=>`<div class="item"><div class="row"><strong>${a.action}</strong><span class="badge">${a.date}</span></div><div class="muted">${a.user} • ${a.detail||"-"}</div></div>`).join("")||`<p class="muted">Aucun log</p>`;
  const low=data.products.filter(p=>p.stock<5);refs.kpiCa.textContent=ca.toFixed(2);refs.kpiSales.textContent=data.sales.length;refs.kpiBookings.textContent=data.bookings.length;refs.kpiLowStock.textContent=low.length;refs.kpiCustomers.textContent=data.customers.length;
  refs.alerts.innerHTML=`${low.map(p=>`<div class="item"><strong>Stock bas:</strong> ${p.name} (${p.stock})</div>`).join("")||"<p class='muted'>Aucune alerte</p>"}`;
  refs.recentAudit.innerHTML=data.audit.slice(0,8).map(a=>`<div class="item"><div class="row"><strong>${a.action}</strong><span class="muted">${a.user}</span></div></div>`).join("")||"<p class='muted'>Aucune activité</p>";
}
document.addEventListener("DOMContentLoaded",()=>{initRefs();applyTheme();refs.loginBtn.addEventListener("click",login);refs.logoutBtn.addEventListener("click",logout);refs.lockBtn.addEventListener("click",lockSession);refs.themeBtn.addEventListener("click",toggleTheme);refs.pin.addEventListener("keydown",e=>{if(e.key==="Enter")login()});render()});
</script>
</body>
</html>
