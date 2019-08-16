function showPdf(){

PDFJS.workerSrc = '../build/pdf.worker.js';//加载核心库
PDFJS.getDocument(url).then(function getPdfHelloWorld(pdf) {
//
// 获取第一页数据
//
pdf.getPage(1).then(function getPageHelloWorld(page) {
var scale = 1.5;
var viewport = page.getViewport(scale);

//
// Prepare canvas using PDF page dimensions
//
var canvas = document.getElementById('the-canvas');
var context = canvas.getContext('2d');
canvas.height = viewport.height;
canvas.width = viewport.width;

//
// Render PDF page into canvas context
//
var renderContext = {
canvasContext: context,
viewport: viewport
};
page.render(renderContext);
});
});

}
