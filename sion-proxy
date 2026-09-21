export default {
  async fetch(req) {
    const cors = {
      "Access-Control-Allow-Origin": "*",
      "Access-Control-Allow-Methods": "GET,POST,OPTIONS",
    };
    if (req.method === "OPTIONS") return new Response(null, { headers: cors });
    const apiUrl = new URL(req.url).searchParams.get("apiurl");
    if (!apiUrl) return new Response("OK - proxy aktif", { headers: cors });
    try {
      const r = await fetch(apiUrl, { headers: { "User-Agent": "Mozilla/5.0" } });
      const res = new Response(r.body, r);
      res.headers.set("Access-Control-Allow-Origin", "*");
      return res;
    } catch (e) {
      return new Response("Error: " + e.message, { status: 500, headers: cors });
    }
  },
};
